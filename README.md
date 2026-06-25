# DeepGate4: Efficient and Effective Representation Learning for Circuit Design at Scale

## News

- **[Jun. 2026]** 🚀 We are excited to release **TRACE**, the official implementation of **“TRACE: Learning to Compute on Circuit Graphs.”**

  TRACE is a **unified circuit encoder** for learning the functional behavior of diverse circuit representations. We model different types of circuits, including **RTL**, **And-Inverter Graphs (AIGs)**, and **post-mapping netlists**, as a **unified computational graph**, enabling a shared learning framework across abstraction levels and design formats.

  At the model level, TRACE adopts a **Hierarchical Transformer** that better aligns with the structured, step-by-step nature of circuit computation, rather than relying on conventional permutation-invariant message passing. It further introduces **function shift learning**, which simplifies the learning target by modeling the discrepancy between true circuit behavior and a local approximation.

  This release includes code for contrastive and predictive learning across RTL, AIG, and post-mapping netlist graph datasets, together with a  [lightweight tutorial example](https://github.com/zyzheng17/TRACE_DAC26/blob/main/tasks/tutorial/computational_graph/README.md) for understanding the core idea.

  📄 Paper: https://arxiv.org/abs/2509.21886  
  🔗 Code: https://github.com/zyzheng17/TRACE_DAC26  
  🤗 Dataset: https://huggingface.co/datasets/zyzheng23/TRACE_dataset
## Overview
Our paper is avaiable at [Arixv](https://www.arxiv.org/abs/2502.01681) and [OpenReview](https://openreview.net/forum?id=b10lRabU9W).
![Overall Pipeline](./Overall_pipline.png)

## Environment
To install the library `deepgate`, please refer to [python-deepgate](https://github.com/zshi0616/python-deepgate).

## Dataset Preparation
We provide sample raw data and corresponding processed data in `./raw_data` and `./raw_sample_data` respectively.

**To prepare your own data:**
* 1. `cd ./simulator` and `bash ./build.sh`
* 2. prepare your own raw aig data in `./YOUR_RAW_DATA`
* 3. `python ./src/dg_dataset/data_preparation.py --aig_dir ./YOUR_RAW_DATA --save_path ./YOUR_DATASET_DIR`
    
## Training 
You can run experiment with `./run/train_large.sh` and `./run/train_large_baseline.sh`
* `./run/train_large.sh` denotes running model with our updating strategy
* `./run/train_large_baseline.sh` denotes running model with its original strategy

We further offer various baseline models:
* `./run/train_large.sh` offers models with **baseline**(DeepGate2), **plain**(DeepGate3), **sparse**(DeepGate4), **GraphGPS**, **Exphormer** and **DAGformer**
* `./run/train_large_baseline.sh` offers models with **PolarGate**, **DeepGate2**, **GraphGPS**, **Exphormer**, **DAGformer**, **GCN**, **GraphSAGE**, **GAT** and **PNA**

