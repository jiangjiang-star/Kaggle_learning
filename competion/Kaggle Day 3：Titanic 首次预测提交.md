**日期**：2026-08-06
**状态**：✅ 已完成（首次提交成功）
## 1. 今日成果
- 在 Kaggle Notebook 中成功读取 Titanic 数据集
- 完成性别存活率分析：女性 74.2%，男性 18.9%
- 使用随机森林模型训练并预测
- 成功生成 `submission.csv` 并提交至排行榜
## 2. 代码流程回顾
### 2.1 数据加载
```python
train_data = pd.read_csv("/kaggle/input/competitions/titanic/train.csv")
test_data = pd.read_csv("/kaggle/input/competitions/titanic/test.csv")

- 训练集：891 人，12 列（含 `Survived` 标签）
    
- 测试集：418 人，11 列（无 `Survived`，需要预测）
    
```
### 2.2 特征分析问题

```python

women = train_data.loc[train_data.Sex == 'female']["Survived"]
rate_women = sum(women) / len(women)   # 74.2%

- **发现**：性别是强特征，女性存活率远高于男性
    

### 2.3 特征工程

python

features = ["Pclass", "Sex", "SibSp", "Parch"]
X = pd.get_dummies(train_data[features])

- `pd.get_dummies()`：将文字列（Sex）转换为数字（0/1），让模型能处理
    
- 本次仅用了4个特征，后续可加入 Age、Fare、Embarked 等
    
```

### 2.4 模型训练

```python
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(n_estimators=100, max_depth=5, random_state=1)
model.fit(X, y)

- 随机森林 = 100棵决策树投票
    
- `max_depth=5` 限制每棵树最多问5个问题，防止过拟合
    
- `random_state=1` 保证结果可复现
    
```

### 2.5 预测与提交

```python

predictions = model.predict(X_test)
output = pd.DataFrame({'PassengerId': test_data.PassengerId, 'Survived': predictions})
output.to_csv('submission.csv', index=False)

- 生成 Kaggle 要求的格式：两列（PassengerId, Survived）
    
- 下载文件后，在比赛页面“Submit Predictions”上传
    
```
## 3. 核心概念理解

|概念|一句话解释|
|---|---|
|DataFrame|Python 中的 Excel 表格，pandas 的核心数据结构|
|One-Hot Encoding|把文字变成 0/1 列，如 Sex → Sex_male, Sex_female|
|随机森林|多棵决策树投票，少数服从多数|
|`fit(X, y)`|模型从历史数据中学习规律|
|`predict(X)`|用学到的规律预测新数据|

## 4. 踩坑记录

- 之前用本地路径 `/kaggle/input/...` 在本地 Python 运行报 `FileNotFoundError`，因为该路径只存在于 Kaggle 云端
- 解决：直接在 Kaggle Notebook 中运行，或下载数据到本地并修改路径

## 5. 下一步优化方向

    填充缺失值（Age、Embarked 等）
    加入更多特征（Fare、Cabin、Name 中的称谓）
    调整模型参数（n_estimators、max_depth）
    尝试其他模型（逻辑回归、XGBoost）

## 6. 一句话总结

第一次从数据到预测到提交的完整流程，即使分数不高，也已经是真正的竞赛参与者。
