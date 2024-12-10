---
layout: post
author: Xuan Feng
tags: [paper, LLM, distributed training, data / model parallelism]
---

## PTD-P: reading notes

### 1. introduction

- motivation

  1. GPU memory capaity is limited, cannot fit parameters

  2. massive compute operations lead to long training time

     -> **data parallel**?

     small per-GPU batch size harms GPU utilization

     communication cost, maximum number of devices = batch size

     -> **tensor parallel**?

     larger models, more servers, more all-reduce communication

     highly model parallelism, small GEMMs, harms GPU utilization 

     -> **pipeline parallel**? (batch split into microbatches)

     pipeline flush, larger batch size is often necessary

  3. therefore, combination

     data parallelism

     \+ pipeline parallelism across multi-GPU servers

     \+ tensor parallelism within a server

- contribution

  - parallelism methods interact in non-trivial ways
  - interleaved schedule, throughput up under same memory foorprint
  - TODO

### 2. modes of parallelization

#### 2.1 data parallelization

-- PyTorch Distributed: Experiences on Accelerating Data Parallel Training

each node has a copy of the full model, and a sharded piece of input dataset

#### 2.2 pipeline model parallelization

**needs the model to be pretty symmetric**

strict optimizer semantics -> periodic pipeline flushes, to synchronize weight versions for both forward and backward passes

"asynchronous and bounded-staleness approaches such as PipeMare, PipeDream, and PipeDream-2BW do away with flushes completely, but relax weight update semantics. We defer consideration of such schemes to future work." --> don't understand, TODO

##### 2.2.1 default schedule



##### 2.2.2 schedule with interleaved stages



#### 2.3 tensor model parallemlization

magatron

MLP:

two GEMMs + one GeLU non-linearity



### 3. performance analysis of parallelization configs

#### 3.1 notation



#### 3.2 tensor & pipeline



#### 3.3 data + model parallelism



#### 3.4 microbatch size



#### 3.5 activation recomputation



### 4. implementation

#### 4.1 communication optimizations



#### 4.2 computation optimizations



### 5. evaluation



### 6. related work



### 7. discussion and conclusion

