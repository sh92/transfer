Code and data for the EMNLP 2018 paper: [Multi-Source Domain Adaptation with Mixture of Experts](https://arxiv.org/abs/1809.02256)

### Running

(to be updated to python3+ and latest versions of pytorch)

```
cd msda-src
python amazon-chen/senti_unified.py
options: [-h] [--cuda] --encoder ENCODER [--critic CRITIC]
         [--advreg] --train TRAIN --test TEST [--eval_only]
         [--batch_size BATCH_SIZE]
         [--batch_size_d BATCH_SIZE_D] [--max_epoch MAX_EPOCH]
         [--optim OPTIM] [--lr LR] [--lr_d LR_D]
         [--lambda_critic LAMBDA_CRITIC]
         [--noise_radius NOISE_RADIUS]
         [--load_model LOAD_MODEL] [--save_model SAVE_MODEL]
         [--save_image SAVE_IMAGE] [--visualize] [--cond COND]

python amazon-chen/senti_moe.py
options: [-h] [--cuda] --train TRAIN --test TEST [--eval_only]
         [--critic CRITIC] [--batch_size BATCH_SIZE]
         [--batch_size_d BATCH_SIZE_D] [--max_epoch MAX_EPOCH]
         [--lr LR] [--lr_d LR_D] [--lambda_critic LAMBDA_CRITIC]
         [--lambda_gp LAMBDA_GP] [--lambda_moe LAMBDA_MOE]
         [--m_rank M_RANK] [--lambda_entropy LAMBDA_ENTROPY]
         [--load_model LOAD_MODEL] [--save_model SAVE_MODEL]
         [--metric METRIC]

Example hyper-parameters for D,E,K->B (w/o MMD):
  --train dvd,electronics,kitchen --test books
  --max_epoch 50 --batch_size 32
  --lambda_moe 0.8 --m_rank 50 --lambda_entropy 0.1
  --lambda_critic 0
```

Note: The official Chen12 dataset doesn't contain a dev split. To perform hyper-parameter selection, you should create multiple folds by randomly splitting dev sets (1/10) from the (multi-source) training data as a means of cross-validation. They follow the same naming convention of `${domain}_dev.svmlight` under the same directory of the training and test sets.

### Dependencies
* Pytorch 0.3
* sklearn
* termcolor
* python 2.X
* CUDA 8.5

### References

```
@InProceedings{guo2018multi,
  author = "Guo, Jiang and Shah, Darsh J and Barzilay, Regina",
  title = "Multi-Source Domain Adaptation with Mixture of Experts",
  booktitle = "Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing",
  year = "2018",
  publisher = "Association for Computational Linguistics",
  pages = "4694--4703",
  location = "Brussels, Belgium",
  url = "http://aclweb.org/anthology/D18-1498"
}
```
