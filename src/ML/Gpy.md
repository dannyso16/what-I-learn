# Gpy

[document](https://gpy.readthedocs.io/en/deploy/)

[gpy.model.gplvm samples](https://programtalk.com/python-examples/GPy.models.GPLVM/)

[gpy notebook](https://nbviewer.jupyter.org/github/SheffieldML/notebook/blob/master/GPy/index.ipynb)

[GPLVMを実行して、潜在空間の座標だけを取り出したい。](https://teratail.com/questions/195736)

[GPy（Pythonのガウス過程用ライブラリ）の使い方](http://statmodeling.hatenablog.com/entry/how-to-use-GPy)

：一通りざっくり試している

[dive into gp](https://www.wouterbulten.nl/blog/tech/diving-into-the-model-with-gpy/)

[Paper With Code: Gaussian Process ](https://paperswithcode.com/task/gaussian-processes)

 [GPyを使ってGPLVMを実行して、潜在空間の座標だけを取り出したい。](https://teratail.com/questions/195736)

```python
# model.X で潜在変数にアクセスできる
import matplotlib.pyplot as plt
%matplotlib inline

spec = oil_flow_dataset["DataTrnLbls"].nonzero()[1]
for c in range(0,3):
    arg = np.where(spec==c)[0]
    plt.plot(model.X[arg,1], model.X[arg,0], '.', c='C'+str(c))
```





## 解説

[PCAの最終形態GPLVMの解説 slideshare](https://www.slideshare.net/antiplastics/pcagplvm)

[The Gaussian Process Latent Variable Model (GPLVM) slideshare](https://www.slideshare.net/jamesmcm03/the-gaussian-process-latent-variable-model-gplvm)

[『ガウス過程と機械学習』サポートページ](http://chasen.org/~daiti-m/gpbook/)