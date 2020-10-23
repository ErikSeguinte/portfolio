---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "What makes the best movie?"
subtitle: "Analyzing data to determine the best movies."
summary: ""
authors: []
tags: []
categories: []
date: 2020-03-03T19:21:02-08:00
lastmod: 2020-03-03T19:21:02-08:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

Using data from Kaggle's [The Movies Dataset](https://www.kaggle.com/rounakbanik/the-movies-dataset), let's determine what makes the best movies.
The Data set gives us ratings from The Movie Database(tMDb), where movies are rated out of 10. And the top 10 movies are:

|ID   | title                           |   vote_average |   vote_count |
|----:|:--------------------------------|---------------:|-------------:|
| 238 | The Godfather                   |            8.5 |         6024 |
| 278 | The Shawshank Redemption        |            8.5 |         8358 |
| 129 | Spirited Away                   |            8.3 |         3968 |
| 155 | The Dark Knight                 |            8.3 |        12269 |
| 240 | The Godfather: Part II          |            8.3 |         3418 |
| 424 | Schindler's List                |            8.3 |         4436 |
| 510 | One Flew Over the Cuckoo's Nest |            8.3 |         3001 |
| 539 | Psycho                          |            8.3 |         2405 |
| 550 | Fight Club                      |            8.3 |         9678 |
| 637 | Life Is Beautiful               |            8.3 |         3643 |

But that's not the whole story. Included in the database is a set of 26,024,289 individual ratings by users. Since we're not making individual movie recomendations -- that's another unit -- let's aggregate the scores into a mean, merge them into the movie database, and see how that compares to the tMDB ratings. After averaging, we get the following top 10.


|ID    | title                              |   rating |   num_votes |
|-----:|:-----------------------------------|---------:|------------:|
|  858 | Sleepless in Seattle               |  4.33981 |       57070 |
|  527 | Once Were Warriors                 |  4.26653 |       67662 |
| 2019 | Hard Target                        |  4.25507 |       13994 |
| 2959 | License to Wed                     |  4.23072 |       60024 |
| 1213 | The Talented Mr. Ripley            |  4.17829 |       33987 |
|  926 | Galaxy Quest                       |  4.17458 |        5453 |
|  296 | Terminator 3: Rise of the Machines |  4.16998 |       87901 |
| 2324 | Local Color                        |  4.16706 |       25245 |
| 1248 | Hannibal Rising                    |  4.15724 |        5199 |
|  950 | Ice Age: The Meltdown              |  4.15008 |        3628 |

It's a very different list, with zero overlap. If only there was a way to scale or combine them. But we're not done yet. There's another way you could define the best movies. And this is the one the studios care about. How much money they made. The Dataset also provides revenue, so let's see what that list looks like.

| ID   | title                                         |     revenue |
|-----:|:----------------------------------------------|------------:|
|  597 | Titanic                                       | 1.84503e+09 |
|  122 | The Lord of the Rings: The Return of the King | 1.11889e+09 |
|   58 | Pirates of the Caribbean: Dead Man's Chest    | 1.06566e+09 |
| 1865 | Pirates of the Caribbean: On Stranger Tides   | 1.04571e+09 |
|  155 | The Dark Knight                               | 1.00456e+09 |
|  671 | Harry Potter and the Philosopher's Stone      | 9.76476e+08 |
|   12 | Finding Nemo                                  | 9.40336e+08 |
|  767 | Harry Potter and the Half-Blood Prince        | 9.33959e+08 |
|  121 | The Lord of the Rings: The Two Towers         | 9.26287e+08 |
| 1893 | Star Wars: Episode I - The Phantom Menace     | 9.24318e+08 |

Another new list. But that's not quite right. The value of a dollar has changed over time. 1 billion 1920 dollars isn't the same as 1 billion 2020 dollars. So using a third dataset provided by the federal government, we can adjust the values based on the year that these movies were released.

|      | title                                         |   adjusted_revenue |
|-----:|:----------------------------------------------|-------------------:|
|   11 | Star Wars                                     |        3.02873e+09 |
|  597 | Titanic                                       |        2.72113e+09 |
|  601 | E.T. the Extra-Terrestrial                    |        1.94532e+09 |
| 1891 | The Empire Strikes Back                       |        1.54683e+09 |
|  329 | Jurassic Park                                 |        1.50785e+09 |
|  122 | The Lord of the Rings: The Return of the King |        1.4399e+09  |
|  238 | The Godfather                                 |        1.38727e+09 |
| 1892 | Return of the Jedi                            |        1.36123e+09 |
| 1893 | Star Wars: Episode I - The Phantom Menace     |        1.31364e+09 |
|  671 | Harry Potter and the Philosopher's Stone      |        1.30554e+09 |

So now we have 3 different metrics with scales that go from 0-5 for one, to billions for another. Which should we use to determine the best movie? With the magic of principle component analysis, we don't have to decide! After waving the PCA wand combining the ratings from 2 different databases along with the adjusted revenue, we get the following top 10 movies.

|      | title                                         |     PCA |
|-----:|:----------------------------------------------|--------:|
|   11 | Star Wars                                     | 8.86514 |
|  597 | Titanic                                       | 7.50724 |
|  601 | E.T. the Extra-Terrestrial                    | 5.27108 |
| 1891 | The Empire Strikes Back                       | 4.81926 |
|  238 | The Godfather                                 | 4.75741 |
|  122 | The Lord of the Rings: The Return of the King | 4.51399 |
|  329 | Jurassic Park                                 | 4.3515  |
| 1892 | Return of the Jedi                            | 4.21927 |
|  121 | The Lord of the Rings: The Two Towers         | 3.98178 |
|  155 | The Dark Knight                               | 3.87451 |

So the original Star Wars is the best movie.

But now that we have this standardized metric, let's have a little fun with it.
It's been said that classic movies are better, and that modern movies are just terrible in comparison.
We can graph time against the PCA rating to see if that's true

{{< figure library="true" src="pca_years.png" title="A caption" lightbox="true" >}}

{{< figure library="true" src="pca_genre.png" title="A caption" lightbox="true" >}}