---
title: "Untitled"
output: html_document
---


```r
library(networkD3)

setwd('/Users/yuki/Documents/code_for_blog/gsw_passing_network')
passes <- read.csv("passes.csv")
groups <- read.csv("groups.csv")
size <- read.csv("size.csv")

passes$source <- as.numeric(as.factor(passes$PLAYER_NAME_LAST_FIRST))-1
passes$target <- as.numeric(as.factor(passes$PASS_TO))-1
passes$PASS <- passes$PASS/50

groups$nodeid <- groups$name
groups$name <- as.numeric(as.factor(groups$name))-1
groups$group <- as.numeric(as.factor(groups$label))-1
nodes <- merge(groups,size[-1],by="id")
nodes$pagerank <- nodes$pagerank^2*100


forceNetwork(Links = passes,
             Nodes = nodes,
             Source = "source",
             fontFamily = "Arial",
             colourScale = JS("d3.scale.category10()"),
             Target = "target",
             Value = "PASS",
             NodeID = "nodeid",
             Nodesize = "pagerank",
             linkDistance = 350,
             Group = "group", 
             opacity = 0.8,
             fontSize = 16,
             zoom = TRUE,
             opacityNoHover = TRUE)
```

<!--html_preserve--><div id="htmlwidget-4908" style="width:504px;height:504px;" class="forceNetwork html-widget"></div>
<script type="application/json" data-for="htmlwidget-4908">{"x":{"links":{"source":[11,11,11,11,11,11,11,11,11,11,11,11,11,11,12,12,12,12,12,12,12,12,12,12,12,12,12,7,7,7,7,7,7,7,7,7,7,7,7,7,13,13,13,13,13,13,13,13,13,13,13,13,13,13,2,2,2,2,2,2,2,2,2,2,14,14,14,14,14,14,14,14,14,14,14,0,0,0,0,0,0,0,0,0,0,0,0,0,0,10,10,10,10,10,10,10,10,10,10,10,10,3,3,3,3,3,3,3,3,3,3,3,3,3,3,6,6,6,6,6,6,6,6,6,6,6,6,6,4,4,4,4,4,4,4,4,4,4,4,4,4,4,5,5,5,5,5,5,5,5,5,5,5,8,8,8,8,8,8,8,8,8,8,8,8,8,8,9,9,9,9,9,9,9,9,1,1,1,1,1,1,1,1,1,1,1,1,1,1],"target":[6,4,3,13,8,12,7,0,2,1,5,10,14,9,8,7,0,3,4,6,13,11,1,5,10,9,14,4,6,8,13,1,12,0,5,2,3,11,10,14,6,4,2,8,7,1,5,12,11,3,0,10,14,9,4,6,13,8,7,1,11,3,0,12,4,0,6,8,7,1,3,13,11,12,9,8,7,12,1,4,6,5,3,11,13,2,10,14,9,8,3,7,0,13,11,6,4,12,5,1,2,12,6,11,7,8,13,10,1,0,5,4,2,9,14,4,13,7,8,1,2,11,3,0,5,12,14,10,6,13,2,7,1,5,11,8,0,12,3,14,10,9,4,8,6,7,0,13,3,1,11,12,10,7,6,0,12,1,13,4,5,2,3,10,11,14,9,3,11,0,8,13,4,1,14,4,8,6,7,13,0,3,2,12,11,5,14,10,9],"value":[3.08,2.9,1.7,1.62,1.54,0.84,0.8,0.72,0.7,0.52,0.3,0.14,0.1,0.06,4.32,2.9,1.88,1.52,1.34,0.98,0.92,0.78,0.76,0.16,0.14,0.02,0.02,7.34,6,5.86,3.26,3.22,2.98,2.92,1.8,1.8,1.18,0.8,0.48,0.28,9.16,5.12,3.66,2.24,2.22,1.9,1.12,0.96,0.8,0.64,0.48,0.34,0.04,0.02,13.44,6.6,4.72,2.18,1.94,1.64,1.08,0.56,0.44,0.02,0.54,0.26,0.22,0.22,0.2,0.14,0.06,0.06,0.04,0.02,0.02,2.94,2.6,1.96,1.44,1.1,1.1,0.86,0.72,0.64,0.56,0.3,0.2,0.2,0.14,1.42,1.14,0.8,0.38,0.34,0.34,0.24,0.22,0.18,0.06,0.04,0.02,1.8,1.42,1.36,1.2,1.16,1.02,0.88,0.86,0.74,0.52,0.42,0.28,0.08,0.02,32.24,13,7.08,6.46,4.14,3.2,3.04,1.86,1.56,1.62,1.02,0.18,0.14,22.32,12.48,8.04,6.08,5.32,2.48,2.38,2.06,1.38,1.34,0.44,0.26,0.1,0.06,4.38,3.16,1.78,1.66,1.38,0.98,0.88,0.48,0.42,0.12,0.06,5.88,5.32,4.62,4.12,3.92,3.08,2.82,1.8,1.72,1.56,1.06,0.94,0.1,0.02,0.22,0.14,0.14,0.08,0.06,0.04,0.02,0.02,6.34,4.2,3.34,2.92,2.58,1.56,1.22,1.18,0.98,0.52,0.46,0.1,0.04,0.02]},"nodes":{"name":["Barbosa, Leandro","Barnes, Harrison","Bogut, Andrew","Clark, Ian","Curry, Stephen","Ezeli, Festus","Green, Draymond","Iguodala, Andre","Livingston, Shaun","Looney, Kevon","McAdoo, James Michael","Rush, Brandon","Speights, Marreese","Thompson, Klay","Varejao, Anderson"],"group":[0,1,1,0,0,1,1,1,0,1,1,1,1,0,1],"nodesize":[52.3611707850441,75.4378963472945,59.7657818859762,35.3958263109262,469.473001117824,23.9527229345031,397.271752130282,151.459584612675,167.106945458715,2.77559132554324,7.30400213603421,31.7317642269105,44.9684206052305,179.54518132615,3.71062155092688]},"options":{"NodeID":"nodeid","Group":"group","colourScale":"d3.scale.category10()","fontSize":16,"fontFamily":"Arial","clickTextSize":40,"linkDistance":350,"linkWidth":"function(d) { return Math.sqrt(d.value); }","charge":-120,"linkColour":"#666","opacity":0.8,"zoom":true,"legend":false,"nodesize":true,"radiusCalculation":" Math.sqrt(d.nodesize)+6","bounded":false,"opacityNoHover":true,"clickAction":null}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->
