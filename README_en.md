# chinese-library-classification
 <span style="color:blue;"><i> A good Python tool for retrieving data from Chinese Library Classification </i></span>
 
## Introduction
------------
This is a Python package for retrieving Chinese book classification data! The Chinese Library Classification (CLC) is a comprehensive classification system published after the founding of the People's Republic of China. It is widely used in libraries and information documentation institutions across the country and is currently in its fifth edition.

During my master's studies, I worked on many projects involving CLC data and found that structured CLC data is relatively difficult to obtain, making certain tasks inconvenient. Therefore, I decided to develop this Python package to allow direct retrieval of CLC data, access hierarchical classification structures, and streamline related workflows.

## Data Source
------------
The [official digital version](http://clc.nlc.cn/ztfdzbjj.jsp) of the Chinese Library Classification (CLC) is also quite difficult to use. Since the goal is to obtain structured CLC data, web scraping is necessary to extract data from existing CLC search platforms.

This Python package collects and integrates CLC data from two sources:
[Site 1](https://ztflh.xhma.com/) 
[Site 2](https://www.clcindex.com/category/)
The web scraping code is available in the project [CLC-data-Scraping](https://github.com/sheoguo/CLC-data-scraping).

## Installation
------------

install via pip (from PyPI):

    pip install chinese-library-classification

## Function

------------


To retrieve relevant information for a specific classification number (where the two links correspond to the pages for this classification number on the respective data scraping websites).

```python
>>> from chinese_library_classification import Chineselibraryclassification
>>> CLC = Chineselibraryclassification()
>>> print(CLC.num2info('A2'))

{"name":"列宁著作","level":2,"link1":"https://ztflh.xhma.com/html/17.html","link2":"https://www.clcindex.com/category/A2/","up_level":"A","next_level":['A21','A22','A23','A25','A26','A28']}


#Retrieve all the parent categories for a given classification number.

>>> print(CLC.num2upper('P455'))

[['P45','天气预报'],['P4','大气科学（气象学）'],['P','天文学、地球科学']]

#Retrieve all the subcategories for a given classification number.
>>> print(CLC.num2next('U655'))

[('U655.1','施工技术管理'),('U655.2','施工组织与设计'),('U655.3','施工设备'),('U655.4','施工技术'),('U655.5','各种工程')]
