* Defining a class in Python
```python
# sales.py
class Sale:
    sale_id: int
    sale_rep_id: int
    sale_amount: float
    commission_pct: int

sale = Sale()
print(sale)
```
* Overriding default constructor
```python
# sales.py
class Sale:
    sale_id: int
    sale_rep_id: int
    sale_amount: float
    commission_pct: int

    def __init__(self):
        print('Inside Constructor')


sale = Sale()
print(sale)
```
* Define custom constructor
```python
# sales.py
class Sale:
    sale_id: int
    sale_rep_id: int
    sale_amount: float
    commission_pct: int


    def __init__(self, sale_id, sale_rep_id, sale_amount, commission_pct):
        self.sale_id = sale_id
        self.sale_rep_id = sale_rep_id
        self.sale_amount = sale_amount
        self.commission_pct = commission_pct


sale = Sale(1, 1, 1500.00, 15)
print(sale)
print(sale.sale_id)
```
* Overriding str and repr methods
```python
# sales.py
class Sale:
    sale_id: int
    sale_rep_id: int
    sale_amount: float
    commission_pct: int

    def __init__(self, sale_id, sale_rep_id, sale_amount, commission_pct):
        self.sale_id = sale_id
        self.sale_rep_id = sale_rep_id
        self.sale_amount = sale_amount
        self.commission_pct = commission_pct

    def __repr__(self):
        return f'{__class__.__name__}<{self.sale_id}>'
    
    def __str__(self):
        return sale.sale_id
```
* Adding additional methods
```python
# sales.py
class Sale:
    sale_id: int
    sale_rep_id: int
    sale_amount: float
    commission_pct: int


    def __init__(self, sale_id, sale_rep_id, sale_amount, commission_pct):
        self.sale_id = sale_id
        self.sale_rep_id = sale_rep_id
        self.sale_amount = sale_amount
        self.commission_pct = commission_pct

    def get_commission_amount(self):
        if self.commission_pct and self.commission_pct < 0:
            raise ValueError
        if self.commission_pct == None:
            return 0.0
        return (self.commission_pct * self.sale_amount) / 100
    
    def get_sale_revenue(self):
        if self.commission_pct and self.commission_pct < 0:
            raise ValueError
        if self.commission_pct == None:
            return self.sale_amount
        return self.sale_amount - self.get_commission_amount()

    def __repr__(self):
        return f'{__class__.__name__}<{self.sale_id}>'
```
* Using Sale from other program
```python
# app.py
from sales import Sale

sale1 = Sale(1, 1, 1500.00, 15)

print(f'Commission Amount for {sale1.sale_id} is {sale1.get_commission_amount()}')
print(f'Net Sale Revenue for {sale1.sale_id} is {sale2.get_sale_revenue()}')

sale2 = Sale(2, 1, 1000.00, None)
print(f'Commission Amount for {sale2.sale_id} is {sale2.get_commission_amount()}')
print(f'Net Sale Revenue for {sale2.sale_id} is {sale2.get_sale_revenue()}')
```