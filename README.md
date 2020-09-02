迅睿CMS模板开发
=================

1. ## 入门教程
    > **1.1.前端页面**
    >> default/home/*.html<br>
    >> default/home/模块目录/*.html

    > **1.2.如何找当前url使用的模板文件**
    >> 修改网站根目录下的index.php文件，找到define('IS_DEV', 0); 修改为1, 然后在浏览器中按F12即可查看效果  
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/ueditor/image/202008/159687654213dfc1.png)

    > **1.3.自定义网站模板**
    >> 新建模板目录：/template/pc/test_html/ （如果创建移动端模板，就建站mobile目录下即可）,test_html目录就是新的模板目录，用于存放html界面的解析文件。<br>
    新建风格目录：/static/test_css/, test_css目录用于存放css和图片资源的
    >> 在后台指定当前网站的模板
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/5b015da4379d9b1.png)

    > **1.4.在后台指定当前网站的模板**
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/379d9b1b6a7644b.png)

    > **1.5固定变量介绍**
    >> 引用css风格目录，{HOME_THEME_PATH} 当前模板风格 /static/风格目录/ , 例如：<br>
    `<link href="{HOME_THEME_PATH}xxxxx.css" rel="stylesheet" type="text/css" />`

    | 常量对照目录表      | 作用                           |
    | ------------------- | ------------------------------ |
    | {HOME_THEME_PATH}   | 当前模板风格 /static/风格目录/ |
    | {ROOT_THEME_PATH}   | 绝对与主站域名的路径           |
    | {THEME_PATH}        | 资源目录/static/               |
    | {MOBILE_THEME_PATH} | 移动端风格目录路径             |
    | {$my_web_url}       | 当前页面的url地址              |
    | {SITE_NAME}         | 当前网站名称                   |
    | {SITE_LOGO}         | 当前网站的logo图片             |
    | {CLIENT_URL}        | 当前终端的域名                 |
    | {MEMBER_URL}        | 用户中心地址                   |


    > **1.6前端模板JS类**
    >> 系统JS函数类，用于/home/***.html模板的表单操作、提交操作、页面点击动作操作、阅读量读取、收藏等动作的支持,放在html的头部head内
    >>
        <!-- 系统关键js(放在head标签内，用到了系统函数时必须引用) -->
        <script type="text/javascript">var is_mobile_cms = '{IS_MOBILE}';</script>
        <script src="{LANG_PATH}lang.js" type="text/javascript"></script>
        <script src="{THEME_PATH}assets/global/plugins/jquery.min.js" type="text/javascript"></script>
        <script src="{THEME_PATH}assets/js/cms.js" type="text/javascript"></script>
        <!-- 系统关键js结束 -->

    > **1.7模板调试信息debug**
    >> 用于循环标签的诊断测试
        例如
        {module *******}
        {/module}
        {$debug}

    >> 当标签自定了return，需要这样改写
        {module ******* return=r}
        {/module}
        {$debug_r}
        会输出这个标签的诊断信息

2. ## 模板文件
    参考官网：http://help.xunruicms.com/6.html<br>
    > **2.1.1网站表单模板**

    >> **2.1.2.网站表单列表页面标签**

    >> **2.1.3.表单内容页标签**

    >> **2.1.4.会员界面**

    >> **2.1.5.后台界面**


    > **2.2.模块相关文件**
    >> **前端界面**<br>
    >> 1、前端显示模板介绍<br>
        模块首页：/template/pc/default/demo/index.html (独立模块才有)<br>
        模块栏目封面：/template/pc/default/demo/category.html<br>
        模块栏目列表：/template/pc/default/demo/list.html<br>
        模块内容：/template/pc/default/demo/show.html<br>
        模块搜索页面：/template/pc/default/demo/search.html<br>
        模块评论页面：/template/pc/default/demo/comment.html comment_ajax.html<br>




3. ## 模板变量
    参考官方：http://help.xunruicms.com/101.html

4. ## 使用
    **3.1模块独立栏目列表循环**
    ```
    {category 
    module=模块目录名称 id=栏目id，pid=指定父级栏目id号，num=显示数量order=inputtime排序
    return=返回变量(默认返回$t)
    
    {/category} 

    例1：指定栏目
    {category module=news id=1}
        <p>栏目名称{$t.name}</p>
        <p>栏目地址{$t.url}</p>
    {/category} 

    例2：循环多个栏目
    {category module=news id=1,2,3}
        <p>栏目名称{$t.name}</p>
        <p>栏目地址{$t.url}</p>
    {/category}

    例3：循环栏目下的子栏目
    {category module=news id=1 return=c1}
        我是父栏目：{$c1.name}<br>
        {category module=news pid=$c1.id return=c2}
            我是{$c1.name}的子栏目：{$c2.name}<br>
        {/category}
    {/category}

    例4：循环某一个栏目里面的文章
    {category module=news id=1}
        {module module=news flag=1 return=t1}
            <p>文章标题{$t1.title}</p>
            <p>文章关键字{$t1.description}</p>
        {/module}
    {/category} 

    ```
    **3.2模块共享栏目列表循环**
    ```
    {category module=share固定参数, id=栏目id，pid=指定父级栏目id号，num=显示数量return=返回变量}
    {/category}

    例1：查询某一个共享栏目
    {category module=share id=1} 
        栏目名称{$t.name}
        栏目地址{$t.url}
        缩略图 {dr_thumb($t.thumb)}
        栏目内容{$t.content}
    {/category}

    例2：查询共享栏目的所有顶级栏目
    {category module=share pid=0} 
        栏目名称{$t.name}
        栏目地址{$t.url}
        缩略图 {dr_thumb($t.thumb)}
        栏目内容{$t.content}
    {/category}

    例3：循环共享栏目下的子栏目
    {category module=share id=1 return=c1}
        我是父栏目：{$c1.name}<br>
        {category module=share pid=$c1.id return=c2}
            我是{$c1.name}的子栏目：{$c2.name}<br>
        {/category}
    {/category}

    
    例4：循环某一个共享栏目里面的文章
    {category module=share id=1}
        {module module=news flag=1 return=t1}
            <p>文章标题{$t1.title}</p>
            <p>文章关键字{$t1.description}</p>
        {/module}
    {/category}

    ```

    **3.3模块内容列表循环**

    **{category  module=模块目录名称 ....}{/category}**
    | category常用参数 | 作用                                                                        |
    | ---------------- | --------------------------------------------------------------------------- |
    | {module}         | 模块目录                                                                    |
    | {id}             | 指定栏目id查询，多个id以,号分开                                             |
    | {pid}            | 指定父级栏目id号                                                            |
    | {more}           | 表示显示数量，支持定点查询，例如1,2表示从第1条记录开始，共显示2条数据       |
    | {num}            | 表示显示数量，不支持定点查询，只能填写整数                                  |
    | {return}         | 默认返回变量为t，调用方式就是{$t.字段值}（多级查询必须设置return=其他字母） |

    
    **{module module=模块名称 ....}{/module}**
    | module常用参数 | 作用                                                                                     |
    | -------------- | ---------------------------------------------------------------------------------------- |
    | {module}       | 模块目录，例如news                                                                       |
    | {catid}        | 栏目id，支持多个栏目以小写分号分开，例如1,2,3,4                                          |
    | {order}        | 排序方式，多个排序以小写分号分开，默认降序排列，例如updatetime_asc表示按更新时间升序排列 |
    | {num}          | 表示显示数量，支持定点查询，例如1,2表示从第1条记录开始，共显示2条数据                    |
    | {flag}         | 推荐位id，多个推荐位用,分隔                                                              |
    | {page}         | 当page=1时表示开启分页查询，否则pagesize与urlrule是不会生效的                            |
    | {pagesize}     | 分页显示数据量（当存在catid时会自动取该栏目设置的数量，修改栏目-模块设置-设置数量即可）  |



    | module常用关键字 | 作用     | category常用关键字   | 作用                     |
    | ---------------- | -------- | -------------------- | ------------------------ |
    | {name}           | 名字     | {name}               | 栏目名称                 |
    | {title}          | 文章标题 | {url}                | 栏目地址                 |
    | {thumb}          | 缩略图   | {dr_thumb($t.thumb)} | 缩略图                   |
    | {description}    | 关键字   | {content}            | 栏目内容                 |
    | {content}        | 内容     | {media}              | 自定义视频字段，后台创建 |
    | {url}            | URL地址  | {catid}              | 栏目id                   |
    | {id}             | 当前id   | {form}               | 自定义来源字段，后台创建 |



    | 常用函数目录表 | 作用       | 例子                              | 参数                                                               |
    | -------------- | ---------- | --------------------------------- | ------------------------------------------------------------------ |
    | {dr_date}      | 获取日期   | {dr_date($t._inputtime, "Y-m-d")} | $_字段名, 'Y-m-d'                                                  |
    | {dr_strcut}    | 截取字符串 | {dr_strcut($t.title,30)}          | $字符串，截取长度                                                  |
    | {dr_thumb}     | 获取缩略图 | {dr_thumb($t)}                    | 图片id, 宽度, 高度, 是否水印, 缩放标准值, 是否下载远程图片进行剪切 |
    | {dr_down_file} | 下载文件   | {dr_down_file($t)}                | $字段名                                                            |
    | {dr_get_file}  | 文件的地址 | {dr_get_file($t)}                 | $字段名                                                            |


4.**文章发布及审核流程**
    <br><br>
    4.1 用户登录后选择内容管理->文章管理-发布内容，填写主题内容后保存内容。<br><br>
    ![RUNOOB 图标](https://s1.ax1x.com/2020/09/02/wSHDL4.png)<br><br>
    4.2 **一审管理员**账户登录后台选择内容->内容审核->文章审核，选择你要的审核的文章。<br><br>
    ![RUNOOB 图标](https://s1.ax1x.com/2020/09/02/wSH6oR.png)<br><br>
    4.3 **二审管理员**账户登录后台选择内容->内容审核->文章审核，选择你要的审核的文章,文章二审后就可以发布了。<br><br>
    ![RUNOOB 图标](https://s1.ax1x.com/2020/09/02/wSHfSK.png)
    
