Copyright (C) 2019 Maker Ecosystem Growth Holdings, INC.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.


GemJoin4 acts
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

GNT acts
```act
behaviour totalSupply of GNT
interface totalSupply()

types:
  Supply : uint256

storage:
  3 |-> Supply

iff
  VCallValue == 0

returns Supply
```
