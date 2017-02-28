---
layout: post
title:  "Note from \"Retail Recommendation Engines with Neo4j\""
excerpt: "Or any graph database, generally"
tags: [graph, "recommender system", note]
permalink: /post/recommender-using-neo4j
---

Webinar: [Neo4j 0228](https://info.neo4j.com/0228-register.html)

I am working on an ecommerce personalization SaaS (think [richrelevance](https://www.richrelevance.com/) or [swiftype](https://swiftype.com/), but with only two backends including me and one data scientist). Don't ask me how to monetize this shit or if this will survive in the cold, harsh world. I care more about how to increase accuracy and decrease response time. Everything else is my secondary concern, including how I will eat tomorrow.

I joined the webinar to find some new ideas and I was expecting something technical and *sciencey*. This is my notes and thoughts on that.

### The Webinar

The introduction talked about how personalized recommendation drives revenue, that you need a relevant and realtime one etc. Everything you expected to hear at an ecommerce recommender system discussion. The speaker gave a brief overview about collaborative filtering and content-based recommendation, also how graph database will help overcoming silo problem.

The demo started with content-based started with importing product data from MySQL and modelling it into graph, creating relations between product, category, and designer. The speaker then proceeded to choose one item *i1* and query for items that have same category, connected category, or same designer. Stuffs easily achievable on MySQL.

Then the speaker imported transaction history, and queried the items to be recommended to user *u1* by finding other items bought by user that bought similar things bought by *u1* which is like three hops. Continued by uploading review data and finding other items reviewed by user that reviewed similar things reviewed by *u1*, similar with the previous part, but this time filtered by the rating of review. Finally speaker uploaded inventory data and created similar query with extra filter for item available in user's location.

On case study: Walmart (transaction history, user interest), Adidas (metadata repository), Ebay (routing), and another unnamed client for something..

On QA session, someone asked the speaker to compare model-based (Netflix problem) with graph-based recommender system and the speaker repeatedly pointed out that the graph one one is realtime with capability to take various other variables like shipping time and availability, compared to the model-based one.

The last point, although not wrong, annoys me.

### My Thoughts

Yes, it's realtime and maybe good enough but I think the batch-running memory-intensive algorithm deserves more love than that. Another thing, "marketing" the whole thing as collaborative filtering, while *by definition* is true, could give a bad name to the *real* matrix-based expensive-yet-suffering-from-cold-start collaborative filtering.

It is hard to create a recommender system, moreover, add "scale" to that. It's not even guaranteed to increase your revenue. I myself haven't proven the one that we develop in real life condition. We are all still new to that, but after all the shits we've been through, it will be dispiriting if someone claims that they've created a personalized recommender system by only using a graph database, and it's better than ours. Maybe this is what scientists are thinking after I bastardize their work and claim that I know recommender system. Ha.

### Verdict

I think this webinar emphazies on graph modelling and is more for managers or developers that want to introduce simple recommender system to their ecommerce.

### Bonus

Not mine, but here's a more advanced version of the webinar content: [https://www.kernix.com/blog/an-efficient-recommender-system-based-on-graph-database_p9](https://www.kernix.com/blog/an-efficient-recommender-system-based-on-graph-database_p9)