```python
install_requires=["openpyxl","pandas"]
```

# Excel Datei einlesen

```
from dataclasses import dataclass
from typing import List
import pandas as pd

@dataclass
class SubGrpZuordRec:
    id:float
    code:str
    LstUqID:float
    LstEntry:str
    new_code:str


# https://stackoverflow.com/questions/53192602/convert-a-pandas-dataframe-into-a-list-of-objects
def get_subgrpzuordrecs_by_xl_file(xl_fp:str)->List[SubGrpZuordRec]:
    df_rows = pd.read_excel(xl_fp)
    return [SubGrpZuordRec(**kwargs) for kwargs in df_rows.to_dict(orient='records')]

```python
