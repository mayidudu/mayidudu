---
layout: post
title:  "Hbase filter!"
date:   2017-04-17 15:29:26 +0800
categories: hbase
---
hbase filter用法
```
scan 'shegong', {FILTER => RowFilter.new(CompareFilter::CompareOp.valueOf('EQUAL'), SubstringComparator.new('ts3'))}
前缀查询
scan 'zmtest1', FILTER => "PrefixFilter('user1')"   
后缀查询
scan 'shegong', {FILTER => RowFilter.new(CompareFilter::CompareOp.valueOf('EQUAL'),RegexStringComparator.new('taobao$')), LIMIT=>5}
```