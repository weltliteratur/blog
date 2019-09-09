---
title: "Using webweb and netwulf with DraCor's API to Generate Interactive Literary Networks"
layout: post
author: [eduard, frank]
comments: true
date: 2019-09-09
---

**DraCor** is the Drama Corpora platform at [**dracor.org**](https://dracor.org/) which holds a growing number of collections of plays of different languages, countries and times (German, Russian, Spanish, Swedish, Roman, Greek, with more to come). All plays are encoded in XML-TEI, but you don't have to meddle with this since the [DraCor API](https://dracor.org/documentation/api/) makes it easy to access structured information, e.g., network data based on the co-occurrence of characters per scene (here's the social network extracted from [Shakespeare's "Hamlet"](https://dracor.org/shake/hamlet#network)).

You can do all kinds of things this network data, e.g., feed them into networ visualisation tools. A couple of weeks ago, [Twitter](https://twitter.com/DanLarremore/status/1161003051726958592) pointed us to two interesting Python packages, **webweb** and **netwulf**:

* **webweb** is "a tool for creating, displaying, and sharing interactive network visualizations on the web" ([DOI:10.21105/joss.01458](http://dx.doi.org/10.21105/joss.01458)),
* **netwulf** is "an interactive visualization tool for networkx Graph-objects, that allows you to produce beautifully looking network visualizations” ([netwulf.readthedocs.io](https://netwulf.readthedocs.io/en/latest/about.html)).

It's really easy to get started and we decided to give these two a spin, thereby also demonstrating the versatility of our DraCor API which provides network data for all TEI-encoded plays of any corpus on the fly.

We prepared [**a Jupyter notebook**](https://github.com/ldsad7/netwulf_and_webweb_for_rusdracor) with the code ready to be executed.

If you want to play with drama networks without doing the legwork, we uploaded some ready-to-use html pages done via **webweb**:

* [Pushkin: Boris Godunov](/webweb/pushkin-boris-godunov.html)
* [Lessing: Emilia Galotti](/webweb/lessing-emilia-galotti.html)
* [Russian Drama Corpus](/webweb/rus.html)
* [German Drama Corpus](/webweb/ger.html)

But let's start to toy around with the other library:

## netwulf

Let's first creat a universal function (```netwulf_representation``` in [our Jupyter Notebook](https://github.com/ldsad7/netwulf_and_webweb_for_rusdracor)).

Then we retrieve the titles of all plays in a corpus (```retrieve_all_plays```).

Now let's take Pushkin's historical play **"Boris Godunov" (c. 1825)** as an example:

```python
# first network: gender groups without labels (other attributes are default)
netwulf_representation('rus', 'pushkin-boris-godunov', group='gender', show_node_labels=False)
```
<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/godunov1.png" alt="Boris Godunov (1)" style="width:500px;" />
</figure>

```python
# second network: gender groups with labels
netwulf_representation('rus', 'pushkin-boris-godunov', group='gender')
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/godunov2.png" alt="Boris Godunov (2)" style="width:500px;" />
</figure>

```python
# third network: isGroup groups with labels
netwulf_representation('rus', 'pushkin-boris-godunov', group='isGroup')
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/godunov3.png" alt="Boris Godunov (3)" style="width:500px;" />
</figure>


```python
# fourth network: gender groups with numOfSpeechActs size without labels
netwulf_representation('rus', 'pushkin-boris-godunov', group='gender', size='numOfSpeechActs', show_node_labels=False)
+ PI
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/godunov4.png" alt="Boris Godunov (4)" style="width:500px;" />
</figure>

By the way, in order to fully regnerate the network (the radii of nodes are not stored by default by netwulf) we need to add a 'size' field to the nodes:

```python
for node in network['nodes']:
    node['size'] = node['radius']
```

As a second example, let's turn to German drama and try the usual suspect, **Lessing's "Emilia Galotti" (1772)**:

```python
# first network: gender groups without labels
netwulf_representation('ger', 'lessing-emilia-galotti', group='gender', show_node_labels=False)  # other attributes are default (see above)
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/galotti1.png" alt="Emilia Galotti (1)" style="width:500px;" />
</figure>

```python
# second network: isGroup groups with labels and degree sizes
netwulf_representation('ger', 'lessing-emilia-galotti', group='isGroup', size='degree')
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/galotti2.png" alt="Emilia Galotti (2)" style="width:500px;" />
</figure>

```python
# third network: gender groups with node and link labels and numOfWords size
netwulf_representation('ger', 'lessing-emilia-galotti', group='gender', size='numOfWords', show_link_labels=True)
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/galotti3.png" alt="Emilia Galotti (3)" style="width:500px;" />
</figure>

```python
# fourth network: all characters with numOfScenes size with node and link labels
netwulf_representation('ger', 'lessing-emilia-galotti', size='numOfSpeechActs')
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/galotti4.png" alt="Emilia Galotti (4)" style="width:500px;" />
</figure>

It is also possible to apply our script to all plays of a corpus (e.g., the Russian one):

```python
playnames = retrieve_all_plays('rus')
for playname in playnames:
    netwulf_representation('rus', playname, size='weightedDegree', group='gender', show_link_labels=True, is_test=True)
```

With this piece of code, netwulf will launch the networks one by one. It will display each network for 5 seconds, followed by a 3-second fade-out before opening the next one. So if you are really bored, you can let hundreds of Russian drama networks pass by your eye. Our collection of currently 190 plays will steal 25 minutes of your time.

## webweb

Dan Larremore's webweb library offers a similar approach to visualise network data (see [documentation](https://webwebpage.github.io/)). We wrote two scripts: the first one is for representing only one play and the second one for representing several plays, e.g., a whole corpus, or translations or different editions of the same play.

We wrote a universal function to integrate DraCor data with webweb (```webweb_representation``` in our [our Jupyter Notebook](https://github.com/ldsad7/netwulf_and_webweb_for_rusdracor)).

As you can see, the script is a bit easier and uses less additional parameters. That is because the library provides us an opportunity to fine-tune the settings such as 'color nodes by'/'scale node sizes' by ourselves in the generated html file. So it is definitely an advantage as you don't have to restart the program.

Other advantages as follows:
1. interactive captions where you can interactively scale the node sizes (although they are limited to 5 ranges),
2. ability to highlight a node (now it is not possible to highlight several nodes, only if these nodes has common letter sequence in their labels which doesn't make sense), using netwulf we can highlight any number of nodes (need to tap twice on each of them),
3. several networks (ability to compare on one page), dynamic networks (ability to see the change over time),
4. ability to color nodes,
5. SVG output.

Though, in our opinion, it has some disadvantages in comparison to the netwulf library:
1. inability to zoom in and out (it leads to inability to predict height and width parameters correctly: every graph is always in the center of the field, so we still need to rerun our program with correct parameters),
2. no possibility to freely change parameters (e.g., colour sets, node radius, etc.) as with netwulf library,
3. some parameters (e.g. link opacity) are binary while in netwulf library they are continuous, some parameters are missing (e.g. stroke width, no 'wiggle' option),
4. inability to restore the graph (not in SVG format) in exact way (saving all the x and y coordinates of the nodes and some other settings), resaving the html doesn't solve the problem.

Let’s look at the graphs produced by WebWeb. First **Pushkin's "Boris Godunov"**:

```python
# first network: gender groups with labels (size == weightedDegree)
```
<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/webweb1.png" alt="webweb (1)" style="width:500px;" />
</figure>

```python
# second network: isGroup groups with labels (size == numOfSpeechActs)
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/webweb2.png" alt="webweb (2)" style="width:500px;" />
</figure>

And now **Lessing's "Emilia Galotti"** again:

```python
# third network: gender groups with labels (size == weightedDegree)
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/webweb3.png" alt="webweb (3)" style="width:500px;" />
</figure>

```python
# fourth network: numOfScenes groups with labels (size == strength)
```

<figure style="text-align:left;">
  <img src="/images/netwulf-webweb/webweb4.png" alt="webweb (4)" style="width:500px;" />
</figure>

Again, the html files generated by webweb embed all the JavaScript you need and you can save them as standalone pages:

* [Pushkin: Boris Godunov](/webweb/pushkin-boris-godunov.html)
* [Lessing: Emilia Galotti](/webweb/lessing-emilia-galotti.html)
* [Russian Drama Corpus](/webweb/rus.html)
* [German Drama Corpus](/webweb/ger.html)
