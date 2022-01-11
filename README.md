# Exploiting Temporal Contexts with Strided Transformer for 3D Human Pose Estimation


This is the official implementation of the approach described in the paper:

> Wenhao Li, Hong Liu, Runwei Ding, Mengyuan Liu, Pichao Wang, and Wenming Yang. [Exploiting Temporal Contexts with Strided Transformer for 3D Human Pose Estimation](https://arxiv.org/pdf/2103.14304). IEEE Transactions on Multimedia, 2022.

<p float="left">
  <img src="figure/skating.gif" width="49%" />
  <img src="figure/dancing.gif" width="49%" />

## Dependencies

- Cuda 11.1
- Python 3.6
- Pytorch 1.7.1

## Dataset setup

Please download the dataset from [Human3.6m](http://vision.imar.ro/human3.6m/) website and refer to [VideoPose3D](https://github.com/facebookresearch/VideoPose3D) to set up the Human3.6M dataset ('./dataset' directory). 

```bash
${POSE_ROOT}/
|-- dataset
|   |-- data_3d_h36m.npz
|   |-- data_2d_h36m_cpn_ft_h36m_dbb.npz
```

## Download pretrained model

The pretrained model can be found in [Google_Drive](https://drive.google.com/drive/folders/1JszQxruPFqux3UzXcJWKgsB67wPk__dH?usp=sharing), please download it and put in the './checkpoint' dictory. 

## Test the model

To test on pretrained model on Human3.6M:

```bash
python main.py --refine --reload --refine_reload --previous_dir 'checkpoint/pretrained'
```

## Train the model

To train on Human3.6M:

```bash
python main.py --train
```

After training for several epoches, add refine module

```bash
python main.py --train --refine --lr 1e-5 --reload --previous_dir [your model saved path]
```

## Citation

If you find our work useful in your research, please consider citing:

    @article{li2022exploiting,
      title={Exploiting temporal contexts with strided transformer for 3d human pose estimation},
      author={Li, Wenhao and Liu, Hong and Ding, Runwei and Liu, Mengyuan and Wang, Pichao and Yang, Wenming},
      journal={IEEE Transactions on Multimedia},
      year={2022},
    }

## Acknowledgement

Our code is built on top of [ST-GCN](https://github.com/vanoracai/Exploiting-Spatial-temporal-Relationships-for-3D-Pose-Estimation-via-Graph-Convolutional-Networks) and is extended from the following repositories. We thank the authors for releasing the codes. 

- [3d-pose-baseline](https://github.com/una-dinosauria/3d-pose-baseline)
- [3d_pose_baseline_pytorch](https://github.com/weigq/3d_pose_baseline_pytorch)
- [VideoPose3D](https://github.com/facebookresearch/VideoPose3D)
- [ST-GCN](https://github.com/vanoracai/Exploiting-Spatial-temporal-Relationships-for-3D-Pose-Estimation-via-Graph-Convolutional-Networks)

## Licence

This project is licensed under the terms of the MIT license.
