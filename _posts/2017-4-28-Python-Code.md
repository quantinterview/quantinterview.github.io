---
layout: post
title: python ����
published: true
---


����һ���ܹ���ʾpython����

```python
from sklearn.metrics import accuracy_score
y_pred = final_gb.predict(testdmat) # Predict using our testdmat
y_pred
```

һ����˵��������ڴ��룬ֻ��Ҫ'����'

����ǳɶεĴ��룬ֻ��Ҫ
'''
����
'''

�����ڴ���ǰ����ĸ��ո��1��TAB

���Ҫ��ʾ�кţ�Ҫ��������﷨
'''
{% codeblock [lang:language] [title] [url] [link text] [start:#] [mark:#,#-#] [linenos:false] %}

code snippet

{% endcodeblock %}
'''

ʾ������
{% codeblock [lang:python] [һС��python����] [url] [link text] [start:#] [mark:#,#-#] [linenos:true] %}

our_params = {'eta': 0.1, 'seed':0, 'subsample': 0.8, 'colsample_bytree': 0.8, 
             'objective': 'binary:logistic', 'max_depth':3, 'min_child_weight':1} 
# Grid Search CV optimized settings

cv_xgb = xgb.cv(params = our_params, dtrain = xgdmat, num_boost_round = 3000, nfold = 5,
                metrics = ['error'], # Make sure you enter metrics inside a list or you may encounter issues!
                early_stopping_rounds = 100) # Look for early stopping that minimizes error

{% endcodeblock %}
