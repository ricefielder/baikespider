# baikespider
BaiKe Spider

scrapy框架写的爬取百度百科的代码

数据库中一共有两张表 一张是实体表entity_table,一张是同名词表synonym_table，数据实体截图放在/picture文件夹下

保存的图片截图也放在/picture下

spider文件夹中的BaiDuSpider是最终的确定的结果，其余的DouBanSpider是开始学习时候看的demo，PictureSpider是开始爬取图片时用来测试的。

BaiDuSpider中有两个Spider 一个是用来获取百科词条的内容（词条名字，简介，相关领域等，可以参看数据库表的截图）和同义词之间的内容

代码内部有详细的注释

主要思想是我们从多个初始节点出发，保存当前页面我们需要保存的信息，然后把页面中的其他词条的链接作为下一跳。Scrapy框架本身有查重机制，我们在保存到数据库时也会再次查重（因为有同名词表）这是entity_table表收集的信息的主要思想

synonym_table表收集的信息的主要思想是从entity_table表中读取每个词条的url，然后保存当前的词条中的第一张词条图片，并改名为OID+编号的形式，OID是实体表entity_table中每项数据的唯一标识,来源于每个词条url后面的item/数字/

具体的操作文档也放在/picture文件夹下
