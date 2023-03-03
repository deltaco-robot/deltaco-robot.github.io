---
title: Sample Tasks
layout: default
nav_order: 2
permalink: sample_tasks
---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Selected Train Tasks
<table style="table-layout: fixed; width: 100%;">
    <tr>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_1/concat.mp4" type="video/mp4"></video></td>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_87/concat.mp4" type="video/mp4"></video></td>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_141/concat.mp4" type="video/mp4"></video></td>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_270/concat.mp4" type="video/mp4"></video></td>
    </tr>
    <tr>
        <td>Task #1: "<i>Put fountain vase in green bin.</i>"</td>
        <td>Task #87: "<i>Put red colored object in red bin.</i>"</td>
        <td>Task #141: "<i>Put chalice shaped object in front bin.</i>"</td>
        <td>Task #270: "<i>Put bottle in right bin.</i>"</td>
    </tr>
</table>

# Selected Test Tasks
<table style="table-layout: fixed; width: 100%;">
    <tr>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_32/concat.mp4" type="video/mp4"></video></td>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_97/concat.mp4" type="video/mp4"></video></td>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_178/concat.mp4" type="video/mp4"></video></td>
        <td><video loop=true autoplay=true width="100%" height="100%" controls><source src="https://www.cs.utexas.edu/users/ml/mturk/videos/taskid_248/concat.mp4" type="video/mp4"></video></td>
    </tr>
    <tr>
        <td>Task #32: "<i>Put black and white colored object in green bin.</i>"</td>
        <td>Task #97: "<i>Put trapezoidal prism shaped object in red bin.</i>"</td>
        <td>Task #178: "<i>Put box sofa in back bin.</i>"</td>
        <td>Task #248: "<i>Put cylinder shaped object in left bin.</i>"</td>
    </tr>
</table>

# Train/Test Splits
<table style="table-layout: fixed; width: 100%;">
    <tr>
        <td><center>Color Split</center></td>
        <td><center>Object Split</center></td>
        <td><center>Shape Split</center></td>
    </tr>
    <tr>
        <td><a href="files/objects_by_color.jpg"><img src="files/objects_by_color.jpg" /></a></td>
        <td><a href="files/objects_by_name.jpg"><img src="files/objects_by_name.jpg" /></a></td>
        <td><a href="files/objects_by_shape.jpg"><img src="files/objects_by_shape.jpg" /></a></td>
    </tr>
</table>

# All Train and Test Tasks
<p><strong>Scenario A (novel objects, colors, and shapes)</strong> trains on all <span style="background-color: #E6E6E6">gray</span> tasks and tests on <span style="background-color: #FFFFE0">yellow</span>, <span style="background-color: #E0E0FF">blue</span>, and <span style="background-color: #E0FFE0">green</span> tasks.</p>
<p><strong>Scenario B (novel colors and shapes)</strong> trains on all <span style="background-color: #E6E6E6">gray</span> and <span style="background-color: #FFFFE0">yellow</span> tasks and tests on <span style="background-color: #E0E0FF">blue</span> and <span style="background-color: #E0FFE0">green</span> tasks.</p>

<a href="files/task_table.png"><img width="50%" src="files/task_table.png" /></a>