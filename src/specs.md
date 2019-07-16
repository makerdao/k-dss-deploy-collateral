```act
behaviour make of GemJoin4
interface make(address usr)

types
  Bag : address

storage
  bags[usr] |-> Bag => _

iff
  VCallValue == 0
  Bag == 0
```
