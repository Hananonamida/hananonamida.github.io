迅睿CMS模板开发
=================

1. **入门教程**
    > **1.1.前端页面**
    >> default/home/*.html

    >> default/home/模块目录/*.html

    > **1.2.如何找当前url使用的模板文件**
    >> 修改网站根目录下的index.php文件，找到define('IS_DEV', 0); 修改为1, 然后在浏览器中按F12即可查看效果  
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/ueditor/image/202008/159687654213dfc1.png)

    > **1.3.自定义网站模板**
    >> 新建模板目录：/template/pc/test_html/ （如果创建移动端模板，就建站mobile目录下即可）,test_html目录就是新的模板目录，用于存放html界面的解析文件。新建风格目录：/static/test_css/, test_css目录用于存放css和图片资源的
    >> 在后台指定当前网站的模板
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/5b015da4379d9b1.png)

    > **1.4.在后台指定当前网站的模板**
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/379d9b1b6a7644b.png)

    > **1.5固定变量介绍**
    >> 引用css风格目录，{HOME_THEME_PATH} 当前模板风格 /static/风格目录/ ,
    `<link href="{HOME_THEME_PATH}xxxxx.css" rel="stylesheet" type="text/css" />`

    |  常量对照目录表| 作用 |
    |  ----  | ----       |
    | {HOME_THEME_PATH}|当前模板风格 /static/风格目录/ |
    | {ROOT_THEME_PATH}   | 绝对与主站域名的路径 |
    | {THEME_PATH} |资源目录/static/ |
    | {MOBILE_THEME_PATH}      | 移动端风格目录路径 |
    | {$my_web_url}|当前页面的url地址 |
    | {SITE_URL}   |当前网站的url域名 |
    | {SITE_MURL}|当前网站的移动端域名 |
    | {SITE_NAME}|当前网站名称 |
    | {SITE_LOGO}|当前网站的logo图片 |
    | {LANG_PATH}|当前网站的语言包目录 |
    | {CLIENT_URL}|当前终端的域名 |
    | {MEMBER_URL}|用户中心地址
    |{SITE_ICP}| 网站ICP备案号|
    |{SITE_TONGJI}| 网站统计代码|

    > **1.6前端模板JS类**
    >> 系统JS函数类，用于/home/***.html模板的表单操作、提交操作、页面点击动作操作、阅读量读取、收藏等动作的支持,放在html的头部head内
    >>
        `<!-- 系统关键js(放在head标签内，用到了系统函数时必须引用) -->
        <script type="text/javascript">var is_mobile_cms = '{IS_MOBILE}';</script>
        <script src="{LANG_PATH}lang.js" type="text/javascript"></script>
        <script src="{THEME_PATH}assets/global/plugins/jquery.min.js" type="text/javascript"></script>
        <script src="{THEME_PATH}assets/js/cms.js" type="text/javascript"></script>
        <!-- 系统关键js结束 -->`

    > **1.7模板调试信息debug**
    >> 用于循环标签的诊断测试
        例如
        `
        {module *******}
        {/module}
        {$debug}`

    >> 当标签自定了return，需要这样改写
        `
        {module ******* return=r}
        {/module}
        {$debug_r}`
        会输出这个标签的诊断信息

2. **模板文件**
    > **2.1.网站表单模板**
    >> 默认网站表单模板介绍
        发布：/template/pc/default/home/form_post.html
        列表：/template/pc/default/home/form_list.html
        查看：/template/pc/default/home/form_show.html

    >> 自定义网站表单模板介绍
        发布：/template/pc/default/home/form/表单表名_post.html
        列表：/template/pc/default/home/form/表单表名_list.html
        查看：/template/pc/default/home/form/表单表名_show.html

    >> 网站表单URL地址介绍
        发布：{router::form_post_url("表单英文名")}
        列表：{router::form_list_url("表单英文名")}
        查看：{router::form_show_url("表单英文名", 表单id)}

    >> 迅睿CMS模板开发
=================

1. **入门教程**
    > **1.1.前端页面**
    >> default/home/*.html

    >> default/home/模块目录/*.html

    > **1.2.如何找当前url使用的模板文件**
    >> 修改网站根目录下的index.php文件，找到define('IS_DEV', 0); 修改为1, 然后在浏览器中按F12即可查看效果  
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/ueditor/image/202008/159687654213dfc1.png)

    > **1.3.自定义网站模板**
    >> 新建模板目录：/template/pc/test_html/ （如果创建移动端模板，就建站mobile目录下即可）,test_html目录就是新的模板目录，用于存放html界面的解析文件。新建风格目录：/static/test_css/, test_css目录用于存放css和图片资源的
    >> 在后台指定当前网站的模板
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/5b015da4379d9b1.png)

    > **1.4.在后台指定当前网站的模板**
    >> ![RUNOOB 图标](https://file.xunruicms.com/vipfile/201908/379d9b1b6a7644b.png)

    > **1.5固定变量介绍**
    >> 引用css风格目录，{HOME_THEME_PATH} 当前模板风格 /static/风格目录/ ,
    `<link href="{HOME_THEME_PATH}xxxxx.css" rel="stylesheet" type="text/css" />`

    |  常量对照目录表| 作用 |
    |  ----  | ----       |
    | {HOME_THEME_PATH}|当前模板风格 /static/风格目录/ |
    | {ROOT_THEME_PATH}   | 绝对与主站域名的路径 |
    | {THEME_PATH} |资源目录/static/ |
    | {MOBILE_THEME_PATH}      | 移动端风格目录路径 |
    | {$my_web_url}|当前页面的url地址 |
    | {SITE_URL}   |当前网站的url域名 |
    | {SITE_MURL}|当前网站的移动端域名 |
    | {SITE_NAME}|当前网站名称 |
    | {SITE_LOGO}|当前网站的logo图片 |
    | {LANG_PATH}|当前网站的语言包目录 |
    | {CLIENT_URL}|当前终端的域名 |
    | {MEMBER_URL}|用户中心地址
    |{SITE_ICP}| 网站ICP备案号|
    |{SITE_TONGJI}| 网站统计代码|

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

2. **模板文件**
    > **2.1.网站表单模板**
    >> 默认网站表单模板介绍
    >>>    发布：/template/pc/default/home/form_post.html
    >>>    列表：/template/pc/default/home/form_list.html
    >>>    查看：/template/pc/default/home/form_show.html

    >> 自定义网站表单模板介绍
    >>>    发布：/template/pc/default/home/form/表单表名_post.html
    >>>    列表：/template/pc/default/home/form/表单表名_list.html
    >>>    查看：/template/pc/default/home/form/表单表名_show.html

    >> 网站表单URL地址介绍
    >>>    发布：{router::form_post_url("表单英文名")}
    >>>    列表：{router::form_list_url("表单英文名")}
    >>>    查看：{router::form_show_url("表单英文名", 表单id)}

    >> 网站表单列表页面标签
        
        {$form_name} 表单中文名称
        {$form_table} 表单英文名称

        // 表单数据列表分页模式调用方法
        {form form=$form_table page=1 urlrule=$urlrule pagesize=5}
        {router::form_show_url($form_table, $t.id)} 表单内容地址
        {dr_strcut($t.title, 60)} 截取60个字符的标题
        {$t.inputtime} 格式化后的发布日期
        {dr_date($t._inputtime, "Y-m-d")} 自定义发布日期
        {/form}
        {$pages} 分页字符串









