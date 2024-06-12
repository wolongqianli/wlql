# python轻量Flask web开发框架代码

## #导入模块

from flask import Flask, render_template

## #创建Flask实例

app = Flask(__name__)

## #定义路由

@app.route('/')
def index():
    return render_template('index.html')							#index.html应放在同文件夹下的新建文件夹templates里，才能渲染htmls			s

## #是否为主程序运行

if __name__ == '__main__':
    app.run(debug=True)														#debug=True开启代码调试





#""""""也为注释的一种方式



"""

if \_\_name\_\_ ==  "main":

​	...



这个代码在很多情况下会用到，他的作用是判断当前脚本是否作为主程序运行，新手理解起来可能比较困难，换句话来说就是py文件在不被导入,如import text,在导入text.py的文件下的情况下，if name ==  "main":下的代码在主程序不会被执行



代码示例：

文件名：text1.py

print("Hello")

if \_\_name\_\_ == "\_\_main\_\_":
    print("Hi")

文件名：text2.py

import text1		 #text1.py和text2.py要在同一个文件夹下

运行

输出Hello

可见并没有输出Hi

"""

