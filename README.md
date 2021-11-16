### CS2309 Research Proposal 

This Repo is the source code for my CS2309 Research Proposal Pilot Test. In the research proposal, I proposed a Robust Knowledge Graph Embedding which is based on Duration Modelling.

#### Dataset

The dataset that we used in our inital experiment is uploaded to Google Drive and can be found [here](https://drive.google.com/file/d/1-rAcQ9BFoejBPi1IydsRtLiUIVbFpE0n/view?usp=sharing). Please first create a `data` folder under the project directory, then extract the dataset into the `data` folder.


#### Usage
Train:
```python time_proj.py -name yago_data_neg_sample_5_mar_10 -margin 10 -l1 0.00 -neg_sample 5 -gpu 5 -epoch 2000 -data_type yago -version large -test_freq 5```

Validate:
```python result_eval.py -eval_mode valid -model yago_data_neg_sample_5_mar_10 -test_freq 5```

Test:
1. Restore model checkpoint: ``` python time_proj.py -res_epoch `Best Validation Epoch` -onlyTest -restore -name yago_data_neg_sample_5_mar_10 -margin 10 -l1 0.00 -neg_sample 5 -gpu 0 -data_type yago -version large```
2. Test result: ```python result_eval.py -eval_mode test -test_freq `Best Validation Epoch` -model yago_data_neg_sample_5_mar_10```


#### References:
I implemented my proposed model based on the code skeleton of HyTE model as referenced below. I have improved the HyTE model by adding weights to data while training. The weight is decided by Duration Modelling(Kaplan–Meier estimator).

Dasgupta, S., Ray, S., & Talukdar, P. (2018). Hyte: Hyperplane-based temporally aware knowledge graph embedding. In Proceedings of the 2018 conference on empirical methods in natural language processing (pp. 2001–2011).

Wang, Z., Zhang, J., Feng, J., & Chen, Z. (2014). Knowledge graph embedding by translating on hyperplanes. In Proceedings of the AAAI Conference on Artificial Intelligence.
