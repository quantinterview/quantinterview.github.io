---
layout: post
title: python 代码
published: true
---


测试一下能够显示python代码

```python
from sklearn.metrics import accuracy_score
y_pred = final_gb.predict(testdmat) # Predict using our testdmat
y_pred
```

一般来说，如果行内代码，只需要'代码'

如果是成段的代码，只需要
'''
代码
'''

或者在代码前面加四个空格或1个TAB

如果要显示行号，要用下面的语法
'''
{% codeblock [lang:language] [title] [url] [link text] [start:#] [mark:#,#-#] [linenos:false] %}

code snippet

{% endcodeblock %}
'''

示例如下
{% codeblock [lang:python] [一小段python代码] [url] [link text] [start:#] [mark:#,#-#] [linenos:true] %}

our_params = {'eta': 0.1, 'seed':0, 'subsample': 0.8, 'colsample_bytree': 0.8, 
             'objective': 'binary:logistic', 'max_depth':3, 'min_child_weight':1} 
# Grid Search CV optimized settings

cv_xgb = xgb.cv(params = our_params, dtrain = xgdmat, num_boost_round = 3000, nfold = 5,
                metrics = ['error'], # Make sure you enter metrics inside a list or you may encounter issues!
                early_stopping_rounds = 100) # Look for early stopping that minimizes error

{% endcodeblock %}
