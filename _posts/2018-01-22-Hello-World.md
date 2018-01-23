---
layout: post
title: The Journey Begins
---
**Week One Thoughts**

After completing a rigorous load of pre-work, I finally started my journey into Data Science at Metis.  The course itself matched the pace of the pre-work, with a daunting day one starting with immediate immersion into understanding the scope of required work.  This is exactly what I signed up for.  A fast paced explaination of numerous topics, which allows the individual to fill in the gaps where they may need some extra understanding.

As a brief overview to layout what the whole week looked like the following table should provide some color.

---

Topics | High-Level Explanation
:------ | :----------
`Pandas` | DataFrames, Merging, Grouping
`Git` | Version control, Open Source, what the flow of operations looks like
`Matplotlib` | Brief introduction to its uses and capabilities
`Seaborn` | Brief introduction to its uses and capabilities
`Complexity` | Big O Notation, fundamental understanding and basic components
`Command Line` | What it is, how it is useful, basic functionality
`Jupyter Notebook` | Tips and tricks, basic how-to
`Bash Profiles` | What they are and how they make life easier
`Visualization of Data` | Utilizing Matplotlib, Seaborn, etc
`Shallow and Deep Copy` | How data structures work in Python and where to avoid pitfalls
`Docstrings` | Why they matter, and why you should flatten code
`Hashing` | A brief but deep tutorial on creating a hash function from scratch
`Iterative Design` | How to process the scope of a problem and tackle it
`Vectorized Operations` | When is this beneficial and how to utilize it
`Minimum Viable Product` | The fundamental project view - time, resources, scope

---

This table is just the basics.  It doesn't include the converstations we had with the career services team, investigations, or the time we spent working on our group projects or challenge problems.

---
**Project Benson:** Week one started off with a data project that involved cleaning the terribly messy MTA turnstile data for a Technology Organization looking to host a summer Gala.  With a team of 4, we set off to tackle the daunting task of making the data useable and determining actionable objectives for our client.  The data cleaning process was time consuming, since numerous anomolies existed within it.  Once cleaned we wanted to figure out the highest volume turnstile stations as the first step in our process.  Once we had the total volumes in hand, specifically looking at spring and summer months, we directed our focus to targeting our demographic.  Without the abilitiy to get gender specific technology information for NYC, we decided to go the route of getting geolocation data for the MTA Stations in conjunction with geolocation data for startups and technology companies in the greater Manhattan area.  The first cross section was a map of MTA Stations and two other data sources as a scatter plot using the library gmplot.

---

![Benson Map](/images/Benson_Total_Map.png){:  .center-image}

---

Using this information, and the information we obtained from scrubbing the data for total volumes by station, we plotted a heat map.  The heat map was also through gmplot and the underlying thought was to plot the companies of interest (as the heat map coordinates) against our top 25 stations by volume.  This plot was much more fruitful in terms of focusing our attention to four station locations that were interesting given our demographic.

---

![Benson Heat Map](/images/Benson_Heatmap.png){:  .center-image}

---

After we had the stations narrowed down using the union of the heatmap and the high volume stations, we wanted to make a more granular recommendation to our client.  We specifically set out to look at the data set at a volume by day level.  Ultimately this analysis led us to the conclusion that our client should focus their canvassing efforts on Wednesdays and Thursdays in order to maximize exposure to their target audience.

![Our Recommendations](/images/week-day-recs.png){:  .center-image}
---

**Things I found interesting**

---

Topic | Use
:------ | ------:
`df.groupby` | splitting, applying, combining, transforming
`df.values` | returning an array of the values for future processing


