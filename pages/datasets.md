---
title: Released Datasets
layout: default
nav_order: 5
permalink: datasets
---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Train Datasets (800-900 trajectories per task)
<ul>
	<li><strong>T198</strong>: 198 obj, color, shape tasks: <a href="https://utexas.box.com/s/cm32ez1n4daoiphxnfvojqulpg9aserd">[hdf5 file]</a>. ~48GB.</li>
		<ul><li>Contains task indices: 0-23, 36-44, 50-73, 86-94, 100-123, 136-144, 150-173, 186-194, 200-223, 236-244, 250-273, 286-294</li></ul>
	<li><strong>T48</strong>: 48 obj tasks: <a href="https://utexas.box.com/s/ocf8onjn6zvcmim4qmjzi35rjsnissqh">[hdf5 file]</a>. ~13GB.</li>
		<ul><li>Contains task indices: 24-31, 74-81, 124-131, 174-181, 224-231, 274-281</li></ul>
	<li><strong>T54</strong>: 54 color, shape tasks: <a href="https://utexas.box.com/s/7kg2gapjnc8irsvz99tldbgrgapropxi">[hdf5 file]</a>. ~10GB.</li>
		<ul><li>Contains task indices: 32-35, 45-49, 82-85, 95-99, 132-135, 145-149, 182-185, 195-199, 232-235, 245-249, 282-285, 295-299</li></ul>
</ul>

## Format of Dataset
<ul>
	<li>Each dataset has a data group, under which the dataset attributes (date, env, etc) are stored.</li>
	<li>Under the data group are groups for each task index. Each task index group contains 800-900 demos for that task.</li>
	<li>Each demo contains actions and observations needed for BC/IL training. Rewards and terminals are also included if one desires to train an RL policy.</li>
</ul>

```
root:NXroot
  data:NXgroup
    @date = '3-29-2023'
    @env = 'Widow250PickPlaceGRFBLRObjCSRndDistractorRndTr...'
    @env_info = '{"env_name": "Widow250PickPlaceGRFBLRObjCSRndD...'
    @time = '18:36:50'
    0:NXgroup // This is the task idx
      demo_0:NXgroup
        @num_samples = 30
        actions = float64(30x8)
        env = 'Widow250PickPlaceGRFBLRObjCSRndDistractorRndTrayQuad-v0'
        env_infos:NXgroup
          grasp_success = bool(30)
          grasp_success_target = bool(30)
          num_objs_placed = int64(30)
          place_success = bool(30)
          place_success_target_container = bool(30)
          place_success_target_obj = bool(30)
          place_success_target_obj_target_container = bool(30)
          task_idx = int64(30)
        observations:NXgroup
          container_quadrants_onehot = float64(30x4)
          image = uint8(30x48x48x3)
          object_orientation = float64(30x4)
          object_position = float64(30x3)
          one_hot_task_id = float64(30x300)
          state = float64(30x10)
          target_container_pos_xy = float64(30x2)
          target_container_quadrant_onehot = float64(30x4)
          target_object_pos_xy = float64(30x2)
        rewards = float64(30)
        terminals = bool(30)
      demo_1:NXgroup
        ...
      ...
    1:NXgroup
    ...
```

# Eval/Target Dataset (10 trajectories per task)
These are the same tasks as the 48 + 54 splits in the train datasets, but in a much smaller filesize provided as few-shot target task demonstrations. Since these are much smaller, we use the npy file format so that they are entirely loaded into memory during experiments.
<ul>
	<li><strong>E48 + E54</strong>: <a href="https://utexas.box.com/s/rg28sk6ko7bcsc20nktyen9exndktjlr">[npy file]</a>. ~600MB.</li>
		<ul><li>Contains task indices: 24-35, 45-49, 74-85, 95-99, 124-135, 145-149, 174-185, 195-199, 224-235, 245-249, 274-285, 295-299</li></ul>
</ul>

# Datasets by Experimental Scenario
<table style="table-layout: fixed; width: 100%;">
    <tr>
    	<td><strong>Exp. Scenario</strong></td>
        <td><strong>Train</strong></td>
        <td><strong>Target</strong></td>
        <td><strong>Onehot Oracle Train=Target buffer</strong></td>
    </tr>
    <tr>
    	<td>(A)</td>
    	<td>T198</td>
    	<td>E48 + E54</td>
    	<td>T48 + T54</td>
    </tr>
    <tr>
    	<td>(B)</td>
    	<td>T198 + T48</td>
    	<td>E48 + E54<sup>1</sup></td>
    	<td>T54</td>
    </tr>
</table>

<sup>1</sup>For experimental scenario B, we use the same dataset as experimental scenario A despite only testing on 54 of the dataset's 102 tasks, because the experimental script automatically filters out the target demonstrations from the unused task indices.

# Concatenating datasets
Due to the file size limit of our cloud storage server, some of the table entries above, such as Exp Scenario B, require concatenating two different files on your local machines, such as T198 + T48.

To concatenate, run:
```
python scripts/concatenate_datasets_hdf5.py -e Widow250PickPlaceGRFBLRObjCSRndDistractorRndTrayQuad-v0 -p [paths of downloaded files from above] -d [output dataset folder path]
```

