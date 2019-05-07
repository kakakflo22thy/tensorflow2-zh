
# 初学者入门 TensorFlow 2.0

<table class="tfo-notebook-buttons" align="left">
  <td>
    <a target="_blank" href="https://tensorflow.google.cn/alpha/tutorials/quickstart/beginner"><img src="https://tensorflow.google.cn/images/tf_logo_32px.png" />View on TensorFlow.org</a>
  </td>
  <td>
    <a target="_blank" href="https://colab.research.google.com/github/tensorflow/docs/blob/master/site/en/r2/tutorials/quickstart/beginner.ipynb"><img src="https://tensorflow.google.cn/images/colab_logo_32px.png" />Run in Google Colab</a>
  </td>
  <td>
    <a target="_blank" href="https://github.com/mashangxue/tensorflow2-zh/edit/master/r2/tutorials/quickstart/beginner.md"><img src="https://tensorflow.google.cn/images/GitHub-Mark-32px.png" />View source on GitHub</a>
  </td>
</table>

安装命令：
```
pip install tensorflow-gpu==2.0.0-alpha0
```
要开始，请将TensorFlow库导入您的程序：

```
from __future__ import absolute_import, division, print_function, unicode_literals
import tensorflow as tf
```

加载并准备[MNIST数据集](http://yann.lecun.com/exdb/mnist/)，将样本从整数转换为浮点数：

```
mnist = tf.keras.datasets.mnist

(x_train, y_train), (x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0
```

通过堆叠图层构建`tf.keras.Sequential`模型。选择用于训练的优化器和损失函数：

```
model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(input_shape=(28, 28)),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Dense(10, activation='softmax')
])

model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])
```

训练和评估模型：

```
model.fit(x_train, y_train, epochs=5)

model.evaluate(x_test, y_test)
```

现在，图像分类器在该数据集上的准确度达到约98％。 要了解更多信息，请阅读[TensorFlow教程](https://tensorflow.google.cn/alpha/tutorials/).。