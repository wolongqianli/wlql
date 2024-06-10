# 标题：训练一个图像识别的ai模型

 

 

## 源码：

import numpy as np

import matplotlib.pyplot as plt

from tensorflow.keras.datasets import mnist

 

## \# 加载数据

(train_images, train_labels), (test_images, test_labels) = mnist.load_data("D://mnist.npz")

print("1"*9999)

 

## \# 归一化数据

train_images = train_images / 255.0

test_images = test_images / 255.0

print("1"*9999)

 

## \# 将图像数据扁平化为向量

train_images = train_images.reshape((-1, 784))

test_images = test_images.reshape((-1, 784))

print("1"*9999)

 

from tensorflow.keras.models import Sequential

from tensorflow.keras.layers import Dense

 

## \# 创建一个简单的神经网络模型

model = Sequential([

  Dense(64, activation='relu', input_shape=(784,)),

  Dense(64, activation='relu'),

  Dense(10, activation='softmax')  # 输出层用softmax激活函数，因为有10个类别

])

print("1"*9999)

 

## \# 编译模型

model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

print("1"*9999)

 

## \# 训练模型

model.fit(train_images, train_labels, epochs=5, batch_size=32)

print("1"*9999)

 

## \# 测试模型性能

test_loss, test_acc = model.evaluate(test_images, test_labels)

print('test accuracy:', test_acc)

 

plt.plot(model.history.history['accuracy'], label='accuracy')

plt.plot(model.history.history['val_accuracy'], label='val_accuracy')

plt.xlabel('epoch')

plt.ylabel('accuracy')

plt.ylim([0, 1])

plt.legend(loc='lower right')

plt.show()

print("1"*9999)

 

## \# 做出预测

predictions = model.predict(test_images[:5])  # 只取前5个测试图片进行预测

predicted_labels = np.argmax(predictions, axis=1)  # 获得预测的标签索引

 

print("predicted labels:", predicted_labels)
