**日期**：2026-09-05  
**状态**：✅ 已完成整个课程
## 1. 今日成果
- ✅ 完成 Kaggle “Intro to Machine Learning” 最后两部分：随机森林回归与参与比赛。
- ✅ 使用随机森林模型在完整训练集上训练，并生成测试集预测。
- ✅ 成功生成 `submission.csv` 并提交至 Kaggle 比赛（房价预测）。
- ✅ 理解了从数据到最终预测的完整机器学习流程。

## 2. 核心知识

### 2.1 随机森林（Random Forest）
- **是什么**：由多棵决策树组成的集成学习模型，通过投票或平均来降低过拟合。
- **为什么比单棵决策树好**：决策树容易过拟合，随机森林通过“随机性”和“多树投票”提升泛化能力。
- **关键参数**：
  - `n_estimators`：树的数量，越多通常越稳定但计算量更大。
  - `max_depth`：树的深度限制，控制过拟合。
  - `max_leaf_nodes`：叶子节点数限制（我们在课程中调过这个参数）。
  - `random_state`：随机种子，保证结果可复现。

### 2.2 建模完整流程（以房价预测为例）
1. **加载数据**：`pd.read_csv()`
2. **选择特征**：`X = home_data[feature_names]`
3. **定义目标**：`y = home_data.SalePrice`
4. **划分数据**：`train_test_split(X, y, random_state=1)`
5. **训练模型**：`model.fit(train_X, train_y)`
6. **评估验证**：`mean_absolute_error(val_y, model.predict(val_X))`
7. **调参**：循环尝试不同 `max_leaf_nodes`，选择 MAE 最小的值。
8. **最终训练**：用最优参数在**全部数据**上重新训练模型。
9. **预测测试集**：`model.predict(test_X)`
10. **生成提交文件**：`output = pd.DataFrame({'Id': test_data.Id, 'SalePrice': preds})` 然后 `to_csv('submission.csv', index=False)`

### 2.3 随机森林 vs 决策树
| 模型 | 优点 | 缺点 |
|------|------|------|
| 决策树 | 简单、易解释 | 容易过拟合，对噪声敏感 |
| 随机森林 | 泛化能力强，准确率高 | 计算量大，不易解释 |

### 2.4 重要概念回顾
- **过拟合**：模型在训练集上表现极好，但在新数据上表现差。
- **验证集**：用来调参和评估模型，防止过拟合。
- **MAE**：平均绝对误差，衡量预测值与真实值的平均差距，越小越好。
- **random_state**：随机种子，固定后结果可复现。

## 3. 踩坑记录
- **模型与数据混淆**：曾把 `(X, y)` 元组赋值给 `rf_model_on_full_data`，导致 `'tuple' object has no attribute 'fit'`。正确做法是先创建模型对象：`RandomForestRegressor(random_state=1)`，再 `model.fit(X, y)`。
- **`fit` 参数要分开传**：`model.fit(X, y)` 不能写成 `model.fit((X, y))`。
- **`get` 方法使用**：`seen.get(num, 0)` 要带括号和默认值，不能写成 `seen.get != 0`（那是方法对象比较）。
- **数组没有 `.head()`**：NumPy 数组用切片 `[:5]`，DataFrame/Series 才用 `.head()`。
- **过拟合的识别**：训练集预测完美但验证集误差大，需要限制树深度或使用随机森林。

## 4. 下一步计划
- 将课程中学到的流程应用到 **Titanic 竞赛** 或其他 Kaggle 比赛。
- 学习特征工程（处理缺失值、编码分类变量、特征缩放）。
- 尝试更高级模型（XGBoost、LightGBM）。
- 学习交叉验证（Cross-Validation）更稳健地评估模型。
- 继续 ROS2、YOLO、深度学习主线。

## 5. 一句话总结
**“机器学习不仅仅是调包，而是理解数据、选择模型、评估调参、最终预测的完整工程。”**