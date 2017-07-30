# mac��caffe������@�iCPU���p�j

## �O����
Xquartz���C���X�g�[������  
https://www.xquartz.org/  
docker���C���X�g�[������  
https://www.docker.com/products/docker-toolbox  

## 1.Docker�N��
```
$ docker run -v ~/test:/workspace -p 888:22 --name "caffe" -d yuki399/caffexorg /usr/sbin/sshd -D
```
*Docker��~�F`$ docker stop caffe`  
*Docker�폜�F`$ docker rm caffe`  
*Docker��`/workspace`�ƃ��[�J��`~/test`���q�����Ă���i~/test��docker�R�}���h���s���������������j  
�Ȃ��A����Docker�ɂ�OpenCV����������Ă���  

## 2.Xquartz���N��
��������uXquartz�v�Ɠ��͂��A�N������  

## 3.Xquartz�̃^�[�~�i�����N��
```
$ ssh -p 888 -YC root@127.0.0.1
```
*����m�F�F`$ xeyes` �����s�B�ڋʂ��\��������OK  

## �T���v�����w�K
### Xquartz�̃^�[�~�i������cifar10�̃f�[�^�Z�b�g�擾
```
$ cd /opt/caffe
$ sh data/cifar10/get_cifar10.sh
$ sh examples/cifar10/create_cifar10.sh
```
### CPU�ݒ�ɏC��  
���L�t�@�C����`solver_mode = CPU`�ɕύX
```
nano examples/cifar10/cifar10_quick_solver.prototxt
nano examples/cifar10/cifar10_quick_solver_lr1.prototxt
```
### �w�K���s
```
$ sh examples/cifar10/train_quick.sh
```
�Ċw�K�܂ōs���A5000��܂Ŋw�K���܂��B  
�ŏI�I��`examples/cifar10/cifar10_quick_iter_5000.caffemodel.h5`���쐬���ďI���ł�

## �摜����
���L�T�C�g�Q��  
http://portaltan.hatenablog.com/entry/2016/02/26/182545
�T���v���Ƃ��ďЉ���T�C�g�͎g�p���Ă��郂�f����4000�i�Ċw�K���Ă��Ȃ����f���j�ł��邱�ƂƁA���ʑO�ɕ��ω����Ă��Ȃ����Ƃ�������������x���グ�邱�Ƃ����҂ł���Ǝv���܂��B