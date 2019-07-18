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

Storage for GemJoin4
```k
syntax Int ::= "#GemJoin4.bags" "[" Int "]" [function]
rule #GemJoin4.bags[A] => #hashedLocation("Solidity", 4, A)
```

Storage for GNT
```k
syntax Int ::= "#GNT.balances" "[" Int "]" [function]
rule #GNT.balances[A] => #hashedLocation("Solidity", 4, A)
```

Storage for Vat
```k
syntax Int ::= "#Vat.wards" "[" Int "]" [function]
rule #Vat.wards[A] => #hashedLocation("Solidity", 0, A)

syntax Int ::= "#Vat.gem" "[" Int "][" Int "]" [function]
rule #Vat.gem[Ilk][Usr] => #hashedLocation("Solidity", 4, Ilk Usr)
```
