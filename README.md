                                             期中作业项目文档
   本次项目实现了基于Note_pad笔记本的一些基本功能的实现，其中分为两个必需功能和两个扩展功能。下面将对这四个功能进行效果展示和关键源码的截图展示<br>
    一 必需功能<br>
    1.时间戳的添加<br>
    由于本笔记一开始缺少时间戳，对其时间戳功能进行添加，以下是其效果图<br>
    ![img_4.png](img_4.png)<br>
     该时间显示的是其更新时间，即会随着时间的更改而变化<br>
     关键代码截图如下：<br>
      ![img_5.png](img_5.png)<br>
      首先先在notelist_item.xml文件种加入文本框布局用于显示时间戳<br>
      ![img_6.png](img_6.png)<br>
     接着在PROJECTION 中添加创建日期和修改日期的列，以便从数据库中获取这些信息。<br>
     ![img_7.png](img_7.png)<br>
     更新 dataColumns 和 viewIDs 数组，SimpleCursorAdapter 映射的是列和视图ID，因此你需要更新数组，以便将时间戳的值显示在 ListView 中。<br>
      ![img_8.png](img_8.png)<br>
     然后，更新 SimpleCursorAdapter 的设置逻辑，使用 Cursor 中的时间戳值，并格式化它们。你可以使用一个 CursorToViewBinder 来处理视图的绑定，这样你就能在绑定数据时格式化时间戳。<br>
     2，搜索功能的添加<br>
    由于该笔记缺少搜索功能，因此在此为笔记添加搜索功能且能以笔记标题或者内容作为关键词进行模糊查询，以下使其效果图<br>
   ![img_9.png](img_9.png)<br>
   打开搜索框<br>
    ![img_10.png](img_10.png)<br>
   根据标题进行搜索<br>
   ![img_11.png](img_11.png)<br>
    ![img_12.png](img_12.png)<br>
   根据内容进行搜索<br>
   关键代码截图如下：<br>
   ![img_13.png](img_13.png)<br>
   在list_options_menu.xml中加入搜索框进行输入搜索<br>
   ![img_14.png](img_14.png)<br>
   菜单中添加一个 SearchView，用于捕捉用户输入并根据输入搜索笔记。<br>
   ![img_15.png](img_15.png)<br>
   创建一个方法来根据搜索条件查询笔记。<br>
   二 附加功能<br>
   1.UI美化<br>
   为笔记本的主页编辑页进行一些UI美化包括：<br>
   1.1.1 字体颜色：标题文字使用了较深的颜色 (#333333)，而日期文字采用了浅灰色 (#999999)，使得层次感更加明显。<br>
   1.1.2 字体大小和加粗：标题文字的大小增大到 18sp，并设置为加粗（textStyle="bold"），让标题更加突出。<br>
   1.1.3 内外边距：通过调整 paddingLeft, paddingRight, 和 paddingTop 来为文本提供更多空间，避免文本紧凑感，并且让布局更舒适。<br>
   1.1.4 行间距：为每个 TextView 添加了 lineSpacingExtra，让文本行间距更加宽松，提升可读性。<br>
   1.1.5 阴影和背景：为整个 LinearLayout 添加了 elevation（阴影效果），让界面看起来更有层次感，背景设置为白色（#FFFFFF），使内容更加突出。<br>
   1.1.6 溢出处理：标题文字使用了 ellipsize="end" 来处理超长文本溢出，避免文字被截断。<br>
   效果图如下<br>
   ![img_16.png](img_16.png)<br>
   对编辑页面进行UI优化包括：<br>
   1.2.1 增加边框和阴影: 使用 elevation 和 background 属性来为 LinedEditText 添加阴影效果，增强其立体感。<br>
   1.2.2 改进字体和颜色: 修改 textColor 和 hintColor 以提高可读性，并为文本设置更好的字体样式。<br>
   1.2.3 调整 padding 和 margin: 优化内外间距，使内容显示更加整齐、舒适。<br>
   1.2.4 优化滚动条和渐变效果: 调整滚动条和渐变效果，使其在长文本时表现更好。<br>
   效果图如下：<br>
   ![img_17.png](img_17.png)<br>
   主要源码如下<br>
   ![img_18.png](img_18.png)<br>
   ![img_19.png](img_19.png)<br>
   2.添加导出笔记功能<br>
   为笔记添加导出笔记功能，可导出到手机的文件中，文件内容包括笔记标题，笔记内容和笔记编辑时间。<br>
   以下为其效果图：<br>
   ![img_22.png](img_22.png)<br>
   ![img_23.png](img_23.png)<br>
    根据路径找到导出文件：<br>
    ![img_24.png](img_24.png)<br>
    ![img_25.png](img_25.png)<br>
     主要代码如下：<br>
     ![img_26.png](img_26.png)<br>
     先在list_context_menu中加入导出笔记的菜单选项<br>
     ![img_20.png](img_20.png)<br>
     这是导出对应内容为txt文件的方法，用于后面导出笔记方法使用<br>
     ![img_21.png](img_21.png)<br>
     这是获取选中笔记ID的方法，用于后面导出笔记方法使用<br>
     ![img_27.png](img_27.png)<br>
     这是获取选中笔记内容的方法，用于后面导出笔记方法使用<br>
     ![img_28.png](img_28.png)<br>
     这是导出笔记的主方法。<br>
      ![img_29.png](img_29.png)<br>
     将导出笔记主方法绑定在内容菜单中进行使用。<br>
      以上为本次期中实验的汇报。
