---

layout: post
title: 网页转换
style: 1

---

#{{ page.title }}#

1.	网页转换定义

	为PC设计的网页，如果直接在手机上予以展示，一定是不能获得最好的用户体验。所以如何针对这些页面，得到一个更适合使用不同尺寸移动设备浏览的页面就是所谓的网页转换。
2.	网页转换分类

	*	第一类，是由网站的管理者刚开始设计时，使用自适应网页设计方法直接对不同尺寸的移动设备进行针对性的排版

		*	如开源的前端自适应页面设计框架 bootstrap，使用到得核心应该就是less 动态css
	*	第二类，是针对已经被设计成不适合移动设备直接进行阅读的页面，这时候需要通过对html代码进行解析，标注，重组等方法，让网页的内容能在移动设备上展现的更美观，简洁。
	
	对于第一类方法，页面内容和结构都是透明的。
	
	而第二类方法则需要通过各种方式去对html代码进行分析，猜测，标注，间接的达到第一类方法的状态。

	也可以理解为第二种方法是对第一种方法的自动化设计。

3.	自动化网页转换方法
	*	模板--半自动化
		
		这种方式与第一类方式比较近似，是用xpass等工具，找到页面中最主要的内容。
	
		对于同一个站点，该站点的主要内容必然在固定的标签内，
		
		所以这种方式最准确，页面效果可控，一般用于对case率较高，或者精品站点来处理。
		
		但是该方法面临的缺点也是显而易见的，
		
		+	配置模板的时间花费较高，针对每一个站点都要总结出所有的页面类型，配置对应的模板
		+	不能迅速的对网站改版作出反应

	
	*	自动化抽取 
		
		针对内容页，如新闻类，博客类，BBS等页面。
		
		这些页面主题内容明确，如标题，时间，来源，以及文章正文，评论等，对于RD来说，需求非常清晰，特征比较鲜明，较容易总结出每种特征所对应的规律，即使是不同的站点，也有较多的共同点可以挖掘
		
		如基于文本密度的征文抽取
	
	*	通用页面转换--视觉分块 
		
		我们看到的网页大多可以分为多个模块，而且可以从多个维度上进行分块
		+	如从视觉上的自上而下，从左到右
		+	还可以根据代码结构，如DOM树，根据统一个父节点下的所有节点当作一块
		+	还可一根据代码习惯，如大多数人写文章会进行分段，那么写HTML代码，也是同样的方式，会在不同意义的段落间加上换行。
		+	如果这个coder不加换行怎么办，也有规律可循，**同一个内容块必然需要用div,p,a,br,table,tr,td,ul li,等等标签进行包裹，而且一般情况下都是有开始，就由闭合，这意味这，在不同块的边界出，必然会同时存在上一个块的闭合标签 ，以及本模块的开始标签，利用这个特性，也可一将原始HTML代码进行分块**
		
		分块后，可以对块进行结构化信息管理，如统计每一块的链接个数，字符树，不同标签的类型，个数，包括语义信息，最终判定该块属于何种类型
		
---
未完成，待补充

针对不同类型的块，使用特殊的CSS样式，并决定哪些块属于关键内容必须输出，那些块属于噪声
	
*	分块的结果我认为可以由多方面的作用
以下总结两点：
	+	现在流行卡片化设计，如WINDOWS Mobile的磁帖，给人的感觉是可定制，层次分明
	+	还有APPLE提出的扁平化设计，去掉了以前拟物化的风格。而且我认为这两者的体验都很不错，更洁大方。
	+	而适合在手机上观看的网页应该是什么样子的，为什么不按照设计APP的思路，去设计一个站点呢，其实某度已经在做了，而且做的很漂亮。但我觉得 可改进的地方

*	分块的准确程度，则是卡片化设计的基础


*	第二个意义在于对搜索结果的反馈，**关键词可以作用到每一块内，可以计算每一块与关键词的相关度，然后输出 相关度较高的块**，而且关键词对于分块的标注也由一定的关系，这一定位文章的主题大概在那些块内。

语义 视觉 代码习惯 代码规律
根据搜索词，或者网页标题，使用相关性，
对每一块进行打分，分数较高这，或者标记较明确的位置作为主要内容输出
		
转换一开始是应该尽量保证不丢内容，做到跟原站风格一致，然后是标记内容，更准确，
最后则可以灵活的控制输出。

在输出的环节，有些关键的HTML代码会极大的影响页面的整洁度

如A标签列表，表格，文字图片混杂等等，这时候需要有特殊的CSS样式来约束这些标签的排列，甚至使用替换某些标签的方式，来改变其排版，尽量使页面更干净整洁，富有层次感

4、意义
	卡片式设计
	搜索引擎---网站级别---卡片级别---效果展示--用户体验
5、方向，趋势
<p>{{ page.date | date_to_string }}</p>