# Disentangled Retrieval and Reasoning for Implicit Question Answering

This repository contains codes for the paper "Disentangled Retrieval and Reasoning for Implicit Question Answering". 

### Disentangled Retrieval Model

1. Creating an Elasticsearch index of our corpus. Following StrategyQA: https://github.com/eladsegal/strategyqa/tree/main/elasticsearch_index
### Disentangled Reasoning Model

#### Dependencies

```
python==3.8
torch==1.9.0
nltk==3.6.8
transformers==4.9.0
```

#### Baseline

The weight model named `weights.th` of baseline should be in the path `./pretrained_model/6_STAR_ORA-p/`, which could be downloaded and unzipped from [here](https://storage.googleapis.com/ai2i/strategyqa/models/6_STAR_ORA-P.tar.gz).

#### Configuration

Run the model with default configuration

```
python main.py
```

Configuration can be edited in the file  `main.py` or in the running command line, for example, 

```
python main.py \
--num_workers 1 \ 
--load_pretrained true \ 
--epoch_num 20 \ 
--batch_size 16 \
--max_length 512 \
--reason_train ./data/reason/train_sents.pk \
--reason_dev ./data/reason/dev_sents.pk \
--reason_test ./data/reason/test_sents.pk \
--prediction_path test_predictions.json \
--model_path ./checkpoints/mymodel.th \
--model_class ReasoningPlain 
```

### Operator

The json files in the path `./classification/` describes several strategies for the definition and classification of operators, which are crucial components in our reasoning. In the paper, we adopt the 5-class strategy, that is, *comparison*, *logical*, *entail*, *numerical* and *binary*. To try another classification strategy, change the configuration `--op_classification` accordingly.

