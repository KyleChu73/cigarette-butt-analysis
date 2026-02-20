# 三大会计准则科目映射表

## 核心科目映射

| 项目 | HKFRS/IFRS | US-GAAP | CN-GAAP（中国准则） | 备注 |
|:-----|:-----------|:--------|:-------------------|:-----|
| **现金及等价物** | Cash and cash equivalents | Cash and cash equivalents | 货币资金 | 核心科目 |
| **短期理财/有价证券** | Financial assets at FVTPL (短期) | Trading investments / Short-term investments | 交易性金融资产 / 其他货币资金 | 需识别期限 |
| **定期存款 (>3 个月)** | Other financial assets | Certificates of deposit | 其他流动资产（需手动识别） | 附注中查找 |
| **应收账款** | Trade receivables | Accounts receivable | 应收账款 | |
| **存货** | Inventories | Inventories | 存货 | |
| **其他流动资产** | Other current assets | Other current assets | 其他流动资产 | |
| **流动资产合计** | Total current assets | Total current assets | 流动资产合计 | |
| **总资产** | Total assets | Total assets | 资产总计 | |
| **短期借款** | Bank borrowings (current) | Short-term debt | 短期借款 | 有息负债 |
| **长期借款** | Bank borrowings (non-current) | Long-term debt | 长期借款 | 有息负债 |
| **有息负债合计** | Total borrowings | Total debt | 有息负债合计 | 短期 + 长期借款 |
| **合同负债/预收款** | Contract liabilities | Deferred revenue | 合同负债 / 预收款项 | 特殊处理 |
| **应付账款** | Trade payables | Accounts payable | 应付账款 | 经营性负债 |
| **其他应付款** | Other payables | Other payables | 其他应付款 | 需关注异常 |
| **总负债** | Total liabilities | Total liabilities | 负债合计 | |
| **净资产/股东权益** | Total equity | Total stockholders' equity | 股东权益合计 | |
| **营业收入** | Revenue | Revenue | 营业收入 | |
| **净利润** | Profit for the year | Net income | 净利润 | |
| **经营性现金流** | Cash flows from operating activities | Net cash provided by operating activities | 经营活动产生的现金流量净额 | |
| **资本性开支** | Purchase of property, plant and equipment | Capital expenditures | 购建固定资产、无形资产和其他长期资产支付的现金 | |
| **自由现金流 (FCF)** | 计算得出 | 计算得出 | 计算得出 | 经营现金流 − 资本开支 |
| **商誉** | Goodwill | Goodwill | 商誉 | |
| **无形资产** | Intangible assets | Intangible assets | 无形资产 | |
| **每股股息** | Dividend per share | Dividend per share | 每股股利 | |
| **总股本** | Number of shares in issue | Shares outstanding | 总股本 | |

---

## T0/T1/T2 计算公式

### T0 计算（最严格）
```
现金池 = 现金及等价物 + 短期理财 + 定期存款 (+ 合同负债，如为白酒等行业)
T0 = 现金池 − 总负债
T0_NAV = T0 / 总股本
```

### T1 计算（中等）
```
有息负债 = 短期借款 + 长期借款
T1 = 现金池 − 有息负债
T1_NAV = T1 / 总股本
```

### T2 计算（宽松）
```
T2 = 现金等价物×1.0 + 应收账款×0.85 + 存货×折扣系数 + 其他流动资产×0.5 − 总负债
T2_NAV = T2 / 总股本
```

**存货折扣系数参考**：
- 白酒/消费品（低报废率）：0.8
- 一般制造业：0.7
- 电子/时尚（高过时风险）：0.5
- 房地产在建项目（接近完工）：0.7

---

## 特殊科目处理规则

### 合同负债（预收款）
- **白酒、饮料等行业**：合同负债本质是客户预付款，经济实质等同于准现金
- **T0/T1 计算**：加入现金池（因为必然转化为收入和现金）
- **T2 计算**：作为负债扣除（保守处理）

### 受限现金
- 受限现金 ≤ 5%：可忽略，正常计入现金池
- 受限现金 5-20%：从 T0/T1 的现金池中剔除受限部分
- 受限现金 > 20%：Fact Check 阶段否决

### 租赁负债（IFRS 16 / ASC 842 之后）
- 经营租赁现已上表
- 将租赁负债纳入有息负债计算

### 质押资产
- 视同有息负债，加入负债端

---

## 财报附注关键查找位置

| 数据项 | 附注位置 |
|:-------|:---------|
| 受限现金 | "货币资金"附注中的"受限资金"段落 |
| 定期存款明细 | "货币资金"或"其他流动资产"附注 |
| 应收账款账龄 | "应收账款"附注中的账龄分析表 |
| 关联方应收 | "关联方交易"附注 |
| 存货构成 | "存货"附注中的分类明细 |
| 商誉减值测试 | "商誉"附注中的减值测试段落 |
| 有息负债明细 | "借款"或"金融负债"附注 |
| 或有负债 | "承诺及或有事项"附注 |
| 资本承诺 | "承诺及或有事项"附注 |
| 对外担保 | "对外担保"或"或有事项"附注 |
| 关联交易 | "关联方关系及其交易"附注 |
| 实控人信息 | "公司基本情况"或"实际控制人"段落 |
| 子公司持股 | "长期股权投资"或"在其他主体中的权益"附注 |

---

## 数据缺失处理

若某科目在财报中缺失或无法确认：
1. 在报告中明确标注「⚠️ 数据缺失：[科目名]」
2. 不得猜测或估算
3. 说明该缺失对分析的影响
