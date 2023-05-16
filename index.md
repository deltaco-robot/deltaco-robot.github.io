---
title: Intro
layout: default
nav_order: 1
permalink: /
---
<center><h1>Using Both Demonstrations and Language Instructions to Efficiently Learn Robotic Tasks</h1></center>
<!-- <center><h3>Multitask robotic policies jointly conditioned on both demonstrations and language</h3></center> -->
<center>ICLR'23</center>
{: .fs-5 .fw-300 }

<center>
<a href="https://scholar.google.com/citations?user=ZzURcb4AAAAJ&hl=en">Albert Yu</a>, <a href="https://www.cs.utexas.edu/~mooney/">Ray Mooney</a><br>
UT Austin<br>
{albertyu, mooney}@utexas.edu<br>
</center>
{: .fs-4 .fw-300 }


## Method Overview
{: .no_toc .text-delta }
<image src="files/overview_fig_v2.1.jpg" />

{: .update }
> <strong>[Training Codebase](https://github.com/Alacarter/deltaco) released! (2023 May 16)</strong>

{: .update }
> <strong>[Human Language Dataset](human_language) released! (2023 Apr 28)</strong>

{: .update }
> <strong>[Environment Codebase](https://github.com/Alacarter/roboverse-deltaco) released! (2023 Apr 1)</strong>

{: .update }
> <strong>[Datasets](datasets) released! (2023 Mar 30)</strong>

{: .update }
> <strong>Code release update (2023 Mar 15)</strong>
>
> We are in the process of cleaning up our code. We plan to make public our environment codebase by the end of March and our training codebase by the end of April. Both will be linked to this website before the ICLR conference.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Motivation
Humans learn new complex tasks often by watching a video, which provides both a visual expert demonstration of how to do the task and also accompanying language instructions (via audio/speech) that help the learner follow along. Learning complex tasks is a lot harder when relying on a single modality (such as only demonstrations or only language instructions). Likewise, for a teacher, it is often harder to clearly specify or teach new tasks with only one modality.

Current multitask policies use task embeddings based on one hot vectors, language embeddings, or demonstration embeddings. However, language instructions and video demonstrations can often be ambiguous, especially if they were provided in environments that do not perfectly align with the environment the robot is evaluated in.

In this work, we show that there exists robotic tasks complex enough where it is beneficial to provide both demonstrations and language instructions, as this is more efficient for both the end-user to specify and also the robot to learn from. Additionally, providing both language embedding features and visual demonstration features helps resolve ambiguities and decrease teacher effort needed when specifying new tasks. This allows the two modalities to contextually complement each other, enabling the robot to more clearly understand what a new task is and how to perform it.

# Contributions
<ol>
    <li>We present DeL-TaCo (Joint <strong><u>De</u></strong>monstration-<strong><u>L</u></strong>anguage <strong><u>Ta</u></strong>sk-<strong><u>Co</u></strong>nditioning), a framework for conditioning a multitask policy simultaneously on both a demonstration and corresponding language instruction.</li>
    <li>We introduce a challenging distribution of hundreds of robotic pick-and-place tasks and show that DeL-TaCo improves generalization ability and significantly decreases the number of expert demonstrations needed when learning novel tasks during test time.</li>
    <li>To our knowledge, this is the first work to show that simultaneously conditioning a multi-task robotic manipulation policy on both demonstration and language embeddings improves sample efficiency and generalization over conditioning on either modality alone.</li>
</ol>