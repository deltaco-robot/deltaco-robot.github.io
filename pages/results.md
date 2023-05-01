---
title: Results
layout: default
nav_order: 4
permalink: results
---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Generalization to Novel Objects, Colors, and Shapes
<table style="table-layout: fixed; width: 100%;">
    <tr>
        <td><a href="files/table1_plot_1_split_0.png"><img width="100%" src="files/table1_plot_1_split_0.png" /></a></td>
        <td><a href="files/table1_plot_1_split_1.png"><img width="100%" src="files/table1_plot_1_split_1.png" /></a></td>
    </tr>
    <tr>
        <td>Training a demo encoder from scratch and using pretrained DistilBERT as the language encoder. <strong>DeL-TaCo (red) achieves 2-3x the generalization performance of SOTA prior works</strong> BC-Z (Jang, et al) and MCIL (Lynch, et al). DeL-TaCo also achieves <strong>better generalization performance than policies conditioned on language-only (blue) or demonstration-only (orange)</strong>, getting closer to the performance of the one-hot oracle policy which was given access to all of the test tasks during training.</td>
        <td>Using pretrained CLIP for the language and demonstration encoder, we still see value in task-conditioning with both demonstrations and language with DeL-TaCo (red) than by learning novel tasks with language alone (blue) or demonstration alone (orange).</td>
    </tr>
</table>

<button type="button" name="button" class="btn" id="btn1" onclick="hideshow('btn1')">View Results as Table</button>
<div id="btn1_table">
  <a href="files/table1.png"><img width="100%" src="files/table1.png" /></a>
</div>

# Generalization to Novel Colors and Shapes
<center><a href="files/table2-3_plot_1_split_0.png"><img width="60%" src="files/table2-3_plot_1_split_0.png" /></a></center>

When trained on all 32 objects and evaluated on only the test colors and shapes, DeL-TaCo outperforms language-only and demonstration-only policies by a <strong>5-11% margin</strong>. Here, we train the demonstration encoder from scratch and use DistilBERT as the language encoder.

<button type="button" name="button" class="btn" id="btn2" onclick="hideshow('btn2')">View Results as Table</button>
<div id="btn2_table">
  <a href="files/table2.png"><img width="100%" src="files/table2.png" /></a>
</div>

# How many Demonstrations is Language Worth?
<center><a href="files/table2-3_plot_1_split_1.png"><img width="60%" src="files/table2-3_plot_1_split_1.png" /></a></center>

To evaluate the value of training policies conditioned on both demonstrations and language, we finetune the demonstration-only policy on <i>k demonstrations per test task</i>, where k is indicated in the legend, and compare it to the performance of DeL-TaCo (red dotted line) which was not given access to any demonstration on any test task. We find that the demonstration-only policy only starts to match the performance of DeL-TaCo when trained on <strong>50 demonstrations per test task</strong>, showing the tremendous value of learning novel tasks with both language and demonstrations. This demonstrates that in situations where demonstrations are collected in environments that do not perfectly align with the environment the robot is evaluated in, <u>providing both demonstrations and language to specify new tasks requires substantially less teacher effort than specifying tasks with either modality alone.</u>

<button type="button" name="button" class="btn" id="btn3" onclick="hideshow('btn3')">View Results as Table</button>
<div id="btn3_table">
  <a href="files/table3.png"><img width="100%" src="files/table3.png" /></a>
</div>

<script>
document.getElementById("btn1_table").style.display = "none";
document.getElementById("btn2_table").style.display = "none";
document.getElementById("btn3_table").style.display = "none";
function hideshow(btn_id) {
  var x = document.getElementById(btn_id + "_table");
  var btn_txt = document.getElementById(btn_id);
  if (x.style.display === "none") {
    x.style.display = "block";
    btn_txt.textContent = "Hide Results as Table";
  } else {
    x.style.display = "none";
    btn_txt.textContent = "View Results as Table";
  }
}
</script>