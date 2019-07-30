```k
rule 0 -Word A => #unsigned(0 -Int A)
  requires #rangeSInt(256, 0 -Int A)
```
