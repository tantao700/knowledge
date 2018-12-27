# 说明
    
- markdown 没有统一标准,不同的网站实现不同
- github 实现的 markdown 语法叫  GFM(Github Favorite Markdown)
- GFM 相对于普通的语法 增加了表格和完成列表的语法
- GFM 没有实现流程图的 markdown 语法

但是有些实现含有流程图语法
```text
```flow
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes 
or No?|approved:>http://www.baidu.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|request

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e


![preview flow](https://image-static.segmentfault.com/334/564/3345641267-59c9df4945ddc_articlex)