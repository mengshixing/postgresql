### 更新表json类型的字段中某一个key的value
+ 例如更新test表的yueyue字段,目前值为{"a":"haohaoxuexi","b":"tiantianxiangshang"}
+ 需要更新"haohaoxuexi"中的"xuexi"替换成"wan"

+ sql语句如下
+ update test set yueyue= jsonb_set(yueyue, array['a'], to_jsonb(regexp_replace(yueyue::json->>'a', 'xuexi', 'wan','g')), false);
#### 主要2个语法糖
+ regexp_replace(yueyue::json->>'a', 'xuexi', 'wan','g') 替换value的值,
+ jsonb_set(jsonb,_text,jsonb,bool) 更新jsonb类型中某个key对应的value的值。
+ 手册https://www.postgresql.org/docs/9.6/functions-json.html
