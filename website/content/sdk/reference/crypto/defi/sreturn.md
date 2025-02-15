---
title: sreturn
description: "Get terra blockchain staking returns history"
keywords:
- blockchain
- terra
- staking
- defi
---

import HeadTitle from '@site/src/components/General/HeadTitle.tsx';

<HeadTitle title="crypto.defi.sreturn - Reference | OpenBB SDK Docs" />

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
<TabItem value="model" label="Model" default>

Get terra blockchain staking returns history [Source: https://fcd.terra.dev/v1]

Source Code: [[link](https://github.com/OpenBB-finance/OpenBBTerminal/tree/main/openbb_terminal/cryptocurrency/defi/terramoney_fcd_model.py#L312)]

```python
openbb.crypto.defi.sreturn(limit: int = 200)
```

---

## Parameters

| Name | Type | Description | Default | Optional |
| ---- | ---- | ----------- | ------- | -------- |
| limit | int | The number of returns to show | 200 | True |


---

## Returns

| Type | Description |
| ---- | ----------- |
| pd.DataFrame | historical staking returns |
---

</TabItem>
<TabItem value="view" label="Chart">

Plots terra blockchain staking returns history [Source: https://fcd.terra.dev/swagger]

Source Code: [[link](https://github.com/OpenBB-finance/OpenBBTerminal/tree/main/openbb_terminal/cryptocurrency/defi/terramoney_fcd_view.py#L254)]

```python
openbb.crypto.defi.sreturn_chart(limit: int = 90, export: str = "", external_axes: Optional[List[matplotlib.axes._axes.Axes]] = None)
```

---

## Parameters

| Name | Type | Description | Default | Optional |
| ---- | ---- | ----------- | ------- | -------- |
| limit | int | Number of records to display | 90 | True |
| export | str | Export dataframe data to csv,json,xlsx file |  | True |
| external_axes | Optional[List[plt.Axes]] | External axes (1 axis is expected in the list), by default None | None | True |


---

## Returns

This function does not return anything

---

</TabItem>
</Tabs>
