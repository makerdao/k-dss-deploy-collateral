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

GemBag acts
```act
behaviour exit of GemBag
interface exit(address usr, uint256 wad)

types
  Ada : address
  Lad : address
  Gem : address GNT
  SrcBalance : uint256
  DstBalance : uint256

storage
  0 |-> Ada
  1 |-> Lad
  2 |-> Gem

storage Gem
  balances[ACCT_ID] |-> SrcBalance => SrcBalance - wad
  balances[usr] |-> DstBalance => DstBalance + wad

iff in range uint256
  SrcBalance - wad
  DstBalance + wad

iff
  VCallValue == 0
  VCallDepth < 1024
  (CALLER_ID == Ada) or (CALLER_ID == Lad)

if
  usr =/= ACCT_ID 

calls
  GNT.transfer  
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

```act
behaviour balanceOf of GNT
interface balanceOf(address src)

types
  Balance : uint256

storage
  balances[src] |-> Balance

iff
  VCallValue == 0

returns Balance
```

```act
behaviour transfer of GNT
interface transfer(address dst, uint wad)

types
  SrcBalance : uint256
  DstBalance : uint256

storage
  balances[CALLER_ID] |-> SrcBalance => SrcBalance - wad
  balances[dst] |-> DstBalance => DstBalance + wad

iff in range uint256
  SrcBalance - wad
  DstBalance + wad

iff
  VCallValue == 0

if
  dst =/= CALLER_ID

returns 1
```

```act
behaviour transfer-self of GNT
interface transfer(address dst, uint wad)

types
  Balance : uint256

storage
  balances[dst] |-> Balance => Balance

iff
  wad <= Balance
  VCallValue == 0

if
  dst == CALLER_ID

returns 1
```
