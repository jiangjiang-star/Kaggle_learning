**日期**：2026-09-07
**状态**：✅ 完成第一课
## 1. 今日成果
- 理解了 DataFrame 是 Pandas 中的二维表格数据结构。
- 学会用字典创建 DataFrame：`pd.DataFrame({'列名': 数据列表})`。
- 学会用 `index` 参数指定行标签。
- 纠正了两个常见语法错误：参数分隔符、字典与参数的混淆。

## 2. 核心知识

### 2.1 DataFrame 是什么？
- DataFrame 是 Pandas 里最核心的数据结构，本质是一张**带标签的二维表格**。
- 每一列是一个 Series，每一行有一个索引。
- 类似 Excel 工作表，是后续所有数据处理的基础。

### 2.2 创建 DataFrame 的正确语法

```python
import pandas as pd

fruit_sales = pd.DataFrame(
    {'Apples': [35, 41], 'Bananas': [21, 34]},
    index=['2017 Sales', '2018 Sales']
)
```
### 具体的指令和参数
pd.read_csv
xxx.shape
xxx.head
xxx.to_csv()

index name colmns index_col
### 注意事项
- 字典内部用冒号 `:`，参数之间用逗号 `,`，参数赋值用等号 `=`。
- **把 `index` 放进字典里**：错误写法 `{'Apples':[35,41], index:[...]}`。正确做法是 `index` 作为 `pd.DataFrame()` 的参数，放在字典外面。
- **`index:` 用冒号**：正确应该用 `index=`，因为它是函数参数，不是字典键值对。
- **参数之间用冒号**：`pd.DataFrame('Apples':[35,41],'Bananas':[21,34])` 是错的，应该用逗号分隔参数。
- **列数据没用字典包住**：`pd.DataFrame('Apples':[35,41])` 不行，必须用 `{'Apples': [35,41]}`。