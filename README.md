迅睿CMS
=================
----------

1. 目录结构
    > 1.前端页面  
    > default/home/*.html
    > default/home/模块目录/*.html

    > 如何找当前url使用的模板文件
    - >> 修改网站根目录下的index.php文件，找到define('IS_DEV', 0); 修改为1, 然后在浏览器中按F12即可查看效果  
    - >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/ueditor/image/202008/159687654213dfc1.png)

    - > 自定义网站模板
    - >> 新建模板目录：/template/pc/test_html/ （如果创建移动端模板，就建站mobile目录下即可）,test_html目录就是新的模板目录，用于存放html界面的解析文件。新建风格目录：/static/test_css/, test_css目录用于存放css和图片资源的
    - >> 在后台指定当前网站的模板
    - >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/5b015da4379d9b1.png)

    - >> 在后台指定当前网站的模板
    - >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/379d9b1b6a7644b.png)


2. 模板文件
    - 第一项嵌套的第一个元素
    - 第一项嵌套的第二个元素
3. 模板变量

+ 第一项
+ 第二项
+ 第三项


- 第一项
- 第二项
- 第三项



