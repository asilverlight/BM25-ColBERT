# BM25-ColBERT
1、拿到msmarco 的训练和dev，默认只有查询和相关文档
2、用bm25给dev retrieve top-1000，给train retrieve top-200，此处retrieve的都是负例
3、看一下retrieve的documents是否包含源数据集的正例，是则挖掉
4、用训练集训练colbert：使用train中bm25返回的top-200中random sample7个
5、训练用🤗的trainer完成，数据处理使用🤗的dataset完成
6、训练好之后，在dev上测试，rerank bm25返回的top-1000，并计算指标