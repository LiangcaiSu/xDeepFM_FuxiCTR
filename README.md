## [FuxiCTR] CTR预估模型的高效、高性能实现（二）
本仓库是便于读者快速上手FuxiCTR而设立，具体实现步骤请参考[原博文](https://zhuanlan.zhihu.com/p/453385054)。
### FuxiCTR
仓库使用的是FuxiCTR v1.1版本，原仓库请参考:
```bash
# FuxiCTR dev version
https://github.com/xue-pai/FuxiCTR
```
FuxiCTR的版权归开发者所有，推荐使用最新版替换仓库中的fuxictr。
### 数据集
仓库提供的数据为采样数据，仅使用于熟悉和试用FuxiCTR框架。
处理过后的全量数据请参考[BARS](https://github.com/openbenchmark/BARS/tree/master/ctr_prediction/datasets#benchmark-datasets)。
博文使用的数据为Criteo_x4_001。
### 运行脚本
依据配置文件训练一个模型:
```bash
nohup python -u main_xdeepfm.py --gpu 0 > logs/xdeepfm_criteo_x4.log & 
```
使用调参工具训练多个模型:

切换到目录tuner下(```cd tuner```)
```bash
nohup python -u run_param_tuner.py --config ../config/xdeepfm_criteo_x4/tuner_xdeepfm_criteo_x4.yaml --gpu 0 1 > ../logs/tuner_xdeepfm_criteo_x4.log & 
```
### 实验结果
以下为使用全量Criteo_x4数据的实验结果，仅供参考。
```bash
 20220104-055623,[command] python run_expid.py --version pytorch --config ../config/xdeepfm_criteo_x4/tuner_xdeepfm_criteo_x4 --expid xDeepFM_criteo_x4_001_1a332027 --gpu 0,[exp_id] xDeepFM_criteo_x4_001_1a332027,[dataset_id] criteo_x4,[train] N.A.,[val] logloss: 0.438579 - AUC: 0.813240,[test] logloss: 0.438173 - AUC: 0.813722
 20220104-095652,[command] python run_expid.py --version pytorch --config ../config/xdeepfm_criteo_x4/tuner_xdeepfm_criteo_x4 --expid xDeepFM_criteo_x4_005_ca239a4e --gpu 0,[exp_id] xDeepFM_criteo_x4_005_ca239a4e,[dataset_id] criteo_x4,[train] N.A.,[val] logloss: 0.439027 - AUC: 0.812783,[test] logloss: 0.438706 - AUC: 0.813151
 20220104-114355,[command] python run_expid.py --version pytorch --config ../config/xdeepfm_criteo_x4/tuner_xdeepfm_criteo_x4 --expid xDeepFM_criteo_x4_006_846e41f2 --gpu 1,[exp_id] xDeepFM_criteo_x4_006_846e41f2,[dataset_id] criteo_x4,[train] N.A.,[val] logloss: 0.438937 - AUC: 0.812833,[test] logloss: 0.438505 - AUC: 0.813312
 20220104-145342,[command] python run_expid.py --version pytorch --config ../config/xdeepfm_criteo_x4/tuner_xdeepfm_criteo_x4 --expid xDeepFM_criteo_x4_008_abbf6472 --gpu 0,[exp_id] xDeepFM_criteo_x4_008_abbf6472,[dataset_id] criteo_x4,[train] N.A.,[val] logloss: 0.438661 - AUC: 0.813146,[test] logloss: 0.438345 - AUC: 0.813516
```
