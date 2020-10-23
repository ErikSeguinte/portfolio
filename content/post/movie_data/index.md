---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "What makes the best movie?"
subtitle: "Analyzing data to determine the best movies."
summary: "Using data to determine a standardized metric and using it to glean insights."
authors: []
tags: ['lambda school', 'data', 'data science', 'build week', 'DSPT5']
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
# The Best Movie
## Rating
Using data from Kaggle's [The Movies Dataset](https://www.kaggle.com/rounakbanik/the-movies-dataset), let's determine what makes the best movies.
The Data set gives us ratings from The Movie Database(tMDb), where movies are rated out of 10. And the top 10 movies are:


<style  type="text/css" ></style>
<table id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5" ><thead>    <tr>        <th class="col_heading level0 col0" >title</th>        <th class="col_heading level0 col1" >vote_average</th>        <th class="col_heading level0 col2" >vote_count</th>    </tr></thead><tbody>
                <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row0_col0" class="data row0 col0" >The Godfather</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row0_col1" class="data row0 col1" >8.50</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row0_col2" class="data row0 col2" >6,024</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row1_col0" class="data row1 col0" >The Shawshank Redemption</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row1_col1" class="data row1 col1" >8.50</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row1_col2" class="data row1 col2" >8,358</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row2_col0" class="data row2 col0" >Spirited Away</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row2_col1" class="data row2 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row2_col2" class="data row2 col2" >3,968</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row3_col0" class="data row3 col0" >The Dark Knight</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row3_col1" class="data row3 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row3_col2" class="data row3 col2" >12,269</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row4_col0" class="data row4 col0" >The Godfather: Part II</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row4_col1" class="data row4 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row4_col2" class="data row4 col2" >3,418</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row5_col0" class="data row5 col0" >Schindler's List</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row5_col1" class="data row5 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row5_col2" class="data row5 col2" >4,436</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row6_col0" class="data row6 col0" >One Flew Over the Cuckoo's Nest</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row6_col1" class="data row6 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row6_col2" class="data row6 col2" >3,001</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row7_col0" class="data row7 col0" >Psycho</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row7_col1" class="data row7 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row7_col2" class="data row7 col2" >2,405</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row8_col0" class="data row8 col0" >Fight Club</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row8_col1" class="data row8 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row8_col2" class="data row8 col2" >9,678</td>
            </tr>
            <tr>
                                <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row9_col0" class="data row9 col0" >Life Is Beautiful</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row9_col1" class="data row9 col1" >8.30</td>
                        <td id="T_3d3cd096_5ea2_11ea_bce8_00155d5a97a5row9_col2" class="data row9 col2" >3,643</td>
            </tr>
    </tbody></table>



## Other Ratings
But that's not the whole story. Included in the database is a set of 26,024,289 individual ratings by users. Since we're not making individual movie recomendations -- that's another unit -- let's aggregate the scores into means, merge them into the movie database, and see how that compares to the tMDB ratings. After averaging, we get the following top 10.

<style  type="text/css" ></style>
<table id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5" ><thead>    <tr>        <th class="col_heading level0 col0" >title</th>        <th class="col_heading level0 col1" >rating</th>        <th class="col_heading level0 col2" >num_votes</th>    </tr></thead><tbody>
                <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row0_col0" class="data row0 col0" >Sleepless in Seattle</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row0_col1" class="data row0 col1" >4.34</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row0_col2" class="data row0 col2" >57,070</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row1_col0" class="data row1 col0" >Once Were Warriors</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row1_col1" class="data row1 col1" >4.27</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row1_col2" class="data row1 col2" >67,662</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row2_col0" class="data row2 col0" >Hard Target</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row2_col1" class="data row2 col1" >4.26</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row2_col2" class="data row2 col2" >13,994</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row3_col0" class="data row3 col0" >License to Wed</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row3_col1" class="data row3 col1" >4.23</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row3_col2" class="data row3 col2" >60,024</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row4_col0" class="data row4 col0" >The Talented Mr. Ripley</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row4_col1" class="data row4 col1" >4.18</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row4_col2" class="data row4 col2" >33,987</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row5_col0" class="data row5 col0" >Galaxy Quest</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row5_col1" class="data row5 col1" >4.17</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row5_col2" class="data row5 col2" >5,453</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row6_col0" class="data row6 col0" >Terminator 3: Rise of the Machines</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row6_col1" class="data row6 col1" >4.17</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row6_col2" class="data row6 col2" >87,901</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row7_col0" class="data row7 col0" >Local Color</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row7_col1" class="data row7 col1" >4.17</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row7_col2" class="data row7 col2" >25,245</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row8_col0" class="data row8 col0" >Hannibal Rising</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row8_col1" class="data row8 col1" >4.16</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row8_col2" class="data row8 col2" >5,199</td>
            </tr>
            <tr>
                                <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row9_col0" class="data row9 col0" >Ice Age: The Meltdown</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row9_col1" class="data row9 col1" >4.15</td>
                        <td id="T_90ada70a_5ea2_11ea_bce8_00155d5a97a5row9_col2" class="data row9 col2" >3,628</td>
            </tr>
    </tbody></table>



## Revenue

It's a very different list, with zero overlap. If only there was a way to scale or combine them. But we're not done yet. There's another way you could define the best movies. And this is the one the studios care about. How much money they made. The Dataset also provides revenue, so let's see what that list looks like.

<style  type="text/css" ></style>
<table id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5" ><thead>    <tr>        <th class="col_heading level0 col0" >title</th>        <th class="col_heading level0 col1" >revenue</th>    </tr></thead><tbody>
                <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row0_col0" class="data row0 col0" >Titanic</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row0_col1" class="data row0 col1" >$1,845,034,188</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row1_col0" class="data row1 col0" >The Lord of the Rings: The Return of the King</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row1_col1" class="data row1 col1" >$1,118,888,979</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row2_col0" class="data row2 col0" >Pirates of the Caribbean: Dead Man's Chest</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row2_col1" class="data row2 col1" >$1,065,659,812</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row3_col0" class="data row3 col0" >Pirates of the Caribbean: On Stranger Tides</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row3_col1" class="data row3 col1" >$1,045,713,802</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row4_col0" class="data row4 col0" >The Dark Knight</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row4_col1" class="data row4 col1" >$1,004,558,444</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row5_col0" class="data row5 col0" >Harry Potter and the Philosopher's Stone</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row5_col1" class="data row5 col1" >$976,475,550</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row6_col0" class="data row6 col0" >Finding Nemo</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row6_col1" class="data row6 col1" >$940,335,536</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row7_col0" class="data row7 col0" >Harry Potter and the Half-Blood Prince</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row7_col1" class="data row7 col1" >$933,959,197</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row8_col0" class="data row8 col0" >The Lord of the Rings: The Two Towers</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row8_col1" class="data row8 col1" >$926,287,400</td>
            </tr>
            <tr>
                                <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row9_col0" class="data row9 col0" >Star Wars: Episode I - The Phantom Menace</td>
                        <td id="T_931146f6_5ea1_11ea_bce8_00155d5a97a5row9_col1" class="data row9 col1" >$924,317,558</td>
            </tr>
    </tbody></table>







### Adjusted Revenue
Another new list. But that's not quite right. The value of a dollar has changed over time. 1 billion 1920 dollars isn't the same as 1 billion 2020 dollars. So using a third dataset provided by the federal government, we can adjust the values based on the year that these movies were released.

<style  type="text/css" >
</style>
<table id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5" ><thead>    <tr>        <th class="col_heading level0 col0" >title</th>        <th class="col_heading level0 col1" >adjusted revenue</th>    </tr></thead><tbody>
                <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row0_col0" class="data row0 col0" >Star Wars</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row0_col1" class="data row0 col1" >$3,028,727,803</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row1_col0" class="data row1 col0" >Titanic</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row1_col1" class="data row1 col1" >$2,721,127,532</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row2_col0" class="data row2 col0" >E.T. the Extra-Terrestrial</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row2_col1" class="data row2 col1" >$1,945,321,985</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row3_col0" class="data row3 col0" >The Empire Strikes Back</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row3_col1" class="data row3 col1" >$1,546,829,516</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row4_col0" class="data row4 col0" >Jurassic Park</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row4_col1" class="data row4 col1" >$1,507,846,186</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row5_col0" class="data row5 col0" >The Lord of the Rings: The Return of the King</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row5_col1" class="data row5 col1" >$1,439,899,368</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row6_col0" class="data row6 col0" >The Godfather</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row6_col1" class="data row6 col1" >$1,387,267,307</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row7_col0" class="data row7 col0" >Return of the Jedi</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row7_col1" class="data row7 col1" >$1,361,232,958</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row8_col0" class="data row8 col0" >Star Wars: Episode I - The Phantom Menace</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row8_col1" class="data row8 col1" >$1,313,638,874</td>
            </tr>
            <tr>
                                <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row9_col0" class="data row9 col0" >Harry Potter and the Philosopher's Stone</td>
                        <td id="T_0fa9bf4c_5ea0_11ea_bce8_00155d5a97a5row9_col1" class="data row9 col1" >$1,305,536,965</td>
            </tr>
    </tbody></table>








## PCA Rating

So now we have 3 different metrics with scales that go from 0-5 for one, to billions for another. Which should we use to determine the best movie? With the magic of principle component analysis, we don't have to decide! After waving the PCA wand combining the ratings from 2 different databases along with the adjusted revenue, we get the following top 10 movies.

| Title                                         |     PCA |
|:----------------------------------------------|--------:|
| Star Wars                                     | 8.86514 |
| Titanic                                       | 7.50724 |
| E.T. the Extra-Terrestrial                    | 5.27108 |
| The Empire Strikes Back                       | 4.81926 |
| The Godfather                                 | 4.75741 |
| The Lord of the Rings: The Return of the King | 4.51399 |
| Jurassic Park                                 | 4.3515  |
| Return of the Jedi                            | 4.21927 |
| The Lord of the Rings: The Two Towers         | 3.98178 |
| The Dark Knight                               | 3.87451 |

So the original Star Wars is the best movie.

# Data Insights

## Movies through the years
It's been said that classic movies are better, and that modern movies are just terrible in comparison.
We can graph time against the PCA rating to see if that's true. And from this graph, it becomes clear that movies hit a high point in the 70s and really took a nose dive in the 2000s

<div>
                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>    
            <div id="b9445eba-2687-418d-a693-d3c293e25226" class="plotly-graph-div" style="height:100%; width:100%;"></div>
            <script type="text/javascript">
                    window.PLOTLYENV=window.PLOTLYENV || {};                   
                if (document.getElementById("b9445eba-2687-418d-a693-d3c293e25226")) {
                    Plotly.newPlot(
                        'b9445eba-2687-418d-a693-d3c293e25226',
                        [{"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "year=%{x}<br>PCA=%{y}", "legendgroup": "", "marker": {"color": "#636efa"}, "name": "", "offsetgroup": "", "orientation": "v", "showlegend": false, "textposition": "auto", "type": "bar", "x": [1915.0, 1925.0, 1927.0, 1930.0, 1931.0, 1932.0, 1933.0, 1934.0, 1936.0, 1937.0, 1939.0, 1940.0, 1941.0, 1942.0, 1944.0, 1945.0, 1946.0, 1948.0, 1949.0, 1950.0, 1951.0, 1952.0, 1953.0, 1954.0, 1955.0, 1956.0, 1957.0, 1958.0, 1959.0, 1960.0, 1961.0, 1962.0, 1963.0, 1964.0, 1965.0, 1966.0, 1967.0, 1968.0, 1969.0, 1970.0, 1971.0, 1972.0, 1973.0, 1974.0, 1975.0, 1976.0, 1977.0, 1978.0, 1979.0, 1980.0, 1981.0, 1982.0, 1983.0, 1984.0, 1985.0, 1986.0, 1987.0, 1988.0, 1989.0, 1990.0, 1991.0, 1992.0, 1993.0, 1994.0, 1995.0, 1996.0, 1997.0, 1998.0, 1999.0, 2000.0, 2001.0, 2002.0, 2003.0, 2004.0, 2005.0, 2006.0, 2007.0, 2008.0, 2009.0, 2010.0, 2011.0, 2012.0, 2013.0, 2014.0, 2015.0], "xaxis": "x", "y": [-0.7315650508108891, 0.20188922332639708, 0.5338956955873393, -0.6073162774839572, 0.37413170028446535, 0.23117685914481903, -0.26324556359417406, 0.3236083584037973, 0.7614689962239016, 0.22887322991578565, 0.37608064661156143, 0.532101075462473, 0.5929551029102678, 0.6238861988149866, 0.5480828610792237, 0.1947940669638344, 0.6136787988295413, 0.5022833962262884, 0.5966306637916882, 0.5468747258455566, 0.12440581253907322, 0.340545957864948, 0.09097083700377656, 0.47566710429423226, 0.28515386159835565, 0.16809646271799367, 0.8712650504425177, 0.45626968959277747, 0.6774536777162394, 0.8728130057428198, 0.1732042397664444, 0.9110689563985003, 0.2595633474530425, 0.47264697529103283, 1.0556482933557527, 0.1444029239401646, 0.5238350949601333, 0.3334907968098052, 0.28723168800830406, -0.8886216603245121, 0.380722264595988, 0.5831491479452787, 0.5299369166118723, 0.5155210663850807, 0.42688687022434363, 0.6791861302748373, 1.7317392799527769, 0.9262151982025765, 0.8374417757712075, 0.3116834659108534, 0.4446605140896237, 0.36064884579741696, 0.04379486908456869, 0.012941910355593975, 0.1534152618730126, -0.3872967237178461, -0.17075921095242694, -0.20457439053903817, 0.06989551010867975, 0.29359522110944436, -0.0662946686711032, 0.030173675897648848, -0.21037300161688707, -0.31533505441818377, 0.19614466626339294, 0.08292650861522863, -0.1362378800301472, -0.11123402522227553, 0.1318225960536406, -0.3101746568741354, 0.043415574123499556, -0.28820692113536983, 0.07498184718666345, 0.09973486023321428, -0.19454664090969756, -0.21093983666164376, -0.2682109449347275, -0.1370004323667159, -0.37109727688212957, -0.6624927711424812, -0.1408813893553318, -1.7331345824398325, -1.3393382200147859, -0.6971951979795359, -1.32972980202716], "yaxis": "y"}],
                        {"barmode": "relative", "legend": {"tracegroupgap": 0}, "template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "PCA rating vs the year"}, "xaxis": {"anchor": "y", "domain": [0.0, 1.0], "title": {"text": "year"}}, "yaxis": {"anchor": "x", "domain": [0.0, 1.0], "title": {"text": "PCA"}}},
                        {"responsive": true}
                    )
                }; 
            </script>
        </div>



<br>


        
<div>
<script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>    
<div id="cfc5b33f-1246-42de-a333-b71b598f969e" class="plotly-graph-div" style="height:100%; width:100%;"></div>
<script type="text/javascript">
window.PLOTLYENV=window.PLOTLYENV || {};
if (document.getElementById("cfc5b33f-1246-42de-a333-b71b598f969e")) {
Plotly.newPlot(
'cfc5b33f-1246-42de-a333-b71b598f969e',
[{"hoverlabel": {"namelength": 0}, "hovertemplate": "year=%{x}<br>PCA=%{y}", "legendgroup": "", "line": {"color": "#636efa", "dash": "solid"}, "mode": "lines", "name": "", "showlegend": false, "type": "scatter", "x": [1915.0, 1925.0, 1927.0, 1930.0, 1931.0, 1932.0, 1933.0, 1934.0, 1936.0, 1937.0, 1939.0, 1940.0, 1941.0, 1942.0, 1944.0, 1945.0, 1946.0, 1948.0, 1949.0, 1950.0, 1951.0, 1952.0, 1953.0, 1954.0, 1955.0, 1956.0, 1957.0, 1958.0, 1959.0, 1960.0, 1961.0, 1962.0, 1963.0, 1964.0, 1965.0, 1966.0, 1967.0, 1968.0, 1969.0, 1970.0, 1971.0, 1972.0, 1973.0, 1974.0, 1975.0, 1976.0, 1977.0, 1978.0, 1979.0, 1980.0, 1981.0, 1982.0, 1983.0, 1984.0, 1985.0, 1986.0, 1987.0, 1988.0, 1989.0, 1990.0, 1991.0, 1992.0, 1993.0, 1994.0, 1995.0, 1996.0, 1997.0, 1998.0, 1999.0, 2000.0, 2001.0, 2002.0, 2003.0, 2004.0, 2005.0, 2006.0, 2007.0, 2008.0, 2009.0, 2010.0, 2011.0, 2012.0, 2013.0, 2014.0, 2015.0], "xaxis": "x", "y": [-0.7315650508108891, 0.20188922332639708, 0.5338956955873393, -0.6073162774839572, 0.37413170028446535, 0.23117685914481903, -0.26324556359417406, 0.3236083584037973, 0.7614689962239016, 0.22887322991578565, 0.37608064661156143, 0.532101075462473, 0.5929551029102678, 0.6238861988149866, 0.5480828610792237, 0.1947940669638344, 0.6136787988295413, 0.5022833962262884, 0.5966306637916882, 0.5468747258455566, 0.12440581253907322, 0.340545957864948, 0.09097083700377656, 0.47566710429423226, 0.28515386159835565, 0.16809646271799367, 0.8712650504425177, 0.45626968959277747, 0.6774536777162394, 0.8728130057428198, 0.1732042397664444, 0.9110689563985003, 0.2595633474530425, 0.47264697529103283, 1.0556482933557527, 0.1444029239401646, 0.5238350949601333, 0.3334907968098052, 0.28723168800830406, -0.8886216603245121, 0.380722264595988, 0.5831491479452787, 0.5299369166118723, 0.5155210663850807, 0.42688687022434363, 0.6791861302748373, 1.7317392799527769, 0.9262151982025765, 0.8374417757712075, 0.3116834659108534, 0.4446605140896237, 0.36064884579741696, 0.04379486908456869, 0.012941910355593975, 0.1534152618730126, -0.3872967237178461, -0.17075921095242694, -0.20457439053903817, 0.06989551010867975, 0.29359522110944436, -0.0662946686711032, 0.030173675897648848, -0.21037300161688707, -0.31533505441818377, 0.19614466626339294, 0.08292650861522863, -0.1362378800301472, -0.11123402522227553, 0.1318225960536406, -0.3101746568741354, 0.043415574123499556, -0.28820692113536983, 0.07498184718666345, 0.09973486023321428, -0.19454664090969756, -0.21093983666164376, -0.2682109449347275, -0.1370004323667159, -0.37109727688212957, -0.6624927711424812, -0.1408813893553318, -1.7331345824398325, -1.3393382200147859, -0.6971951979795359, -1.32972980202716], "yaxis": "y"}],
{"legend": {"tracegroupgap": 0}, "template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "PCA rating vs the year"}, "xaxis": {"anchor": "y", "domain": [0.0, 1.0], "title": {"text": "year"}}, "yaxis": {"anchor": "x", "domain": [0.0, 1.0], "title": {"text": "PCA"}}},
{"responsive": true}
)
};
</script>
</div>




If the Null hypothesis were that movies in 1970 were better than movies in 2000s, we would have to reject it with a calculated P value of $4.54 \times 10^{-05}$

## Genres
But what else might effect a movies ratings? Are adventure movies better than Westerns? Are Romance movies better than comedies?

{{< figure src="pca_genre.png" title="PCA rating of Genres" lightbox="true" >}}

From the data, the clear loser are Foreign Films, and that War movies are a safe bet.

## Budget
How about budgets? Do bigger budgets translate to better movies?

<style  type="text/css" >
</style>
<table id="T_8b702818_6018_11ea_bbe9_0242ac1c0002" ><thead>    <tr>        <th class="blank level0" ></th>        <th class="col_heading level0 col0" >Mean Budget</th>        <th class="col_heading level0 col1" >Mean Revenue</th>        <th class="col_heading level0 col2" >PCA</th>    </tr>    <tr>        <th class="index_name level0" >Budget Category</th>        <th class="blank" ></th>        <th class="blank" ></th>        <th class="blank" ></th>    </tr></thead><tbody>
<tr>
        <th id="T_8b702818_6018_11ea_bbe9_0242ac1c0002level0_row0" class="row_heading level0 row0" >[0, 500,000)</th>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row0_col0" class="data row0 col0" >$197,962</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row0_col1" class="data row0 col1" >$15,368,653</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row0_col2" class="data row0 col2" >-0.15</td>
</tr>
<tr>
        <th id="T_8b702818_6018_11ea_bbe9_0242ac1c0002level0_row1" class="row_heading level0 row1" >[500,000, 40,000,000)</th>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row1_col0" class="data row1 col0" >$18,500,755</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row1_col1" class="data row1 col1" >$61,334,171</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row1_col2" class="data row1 col2" >-0.06</td>
</tr>
<tr>
        <th id="T_8b702818_6018_11ea_bbe9_0242ac1c0002level0_row2" class="row_heading level0 row2" >[40,000,000, 100,000,000)</th>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row2_col0" class="data row2 col0" >$61,415,816</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row2_col1" class="data row2 col1" >$186,069,871</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row2_col2" class="data row2 col2" >0.04</td>
</tr>
<tr>
        <th id="T_8b702818_6018_11ea_bbe9_0242ac1c0002level0_row3" class="row_heading level0 row3" >[100,000,000, 1,000,000,000,000)</th>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row3_col0" class="data row3 col0" >$141,292,135</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row3_col1" class="data row3 col1" >$436,756,768</td>
        <td id="T_8b702818_6018_11ea_bbe9_0242ac1c0002row3_col2" class="data row3 col2" >0.70</td>
</tr>
</tbody></table>









<div>
<script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>    
<div id="05cad4cf-1da3-4884-92f3-986c162f6166" class="plotly-graph-div" style="height:100%; width:100%;"></div>
<script type="text/javascript">
        window.PLOTLYENV=window.PLOTLYENV || {};
if (document.getElementById("05cad4cf-1da3-4884-92f3-986c162f6166")) {
        Plotly.newPlot(
        '05cad4cf-1da3-4884-92f3-986c162f6166',
        [{"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "x=%{x}<br>PCA=%{y}", "legendgroup": "", "marker": {"color": "#636efa"}, "name": "", "offsetgroup": "", "orientation": "v", "showlegend": false, "textposition": "auto", "type": "bar", "x": ["no-budget", "low-budget", "medium-budget", "High-budget:"], "xaxis": "x", "y": [-0.14972424762827316, -0.05958098183317546, 0.038098032355617546, 0.7001137621595251], "yaxis": "y"}],
        {"barmode": "relative", "legend": {"tracegroupgap": 0}, "margin": {"t": 60}, "template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "xaxis": {"anchor": "y", "categoryorder": "array", "domain": [0.0, 1.0], "title": {"text": "Budget vs PCA rating"}}, "yaxis": {"anchor": "x", "domain": [0.0, 1.0], "title": {"text": "PCA"}}},
        {"responsive": true}
        )
};
</script>
</div>

## What else?
Clearly, there are other things that could affect the rating of a movie. Here are possible other insights that might be scraped from the data

* Who is the best director of all time?

* Which movies had the greatest return on investment given their budget and their revenue?

* Should Directors stay in their lane? In other words, are directors who have a body of work that is majority one genre able to switch to a completely different genre and still make movies that are just as good? For example, a renowned Horror director might decide to do a romance film. How do they do? How about the other way around?

