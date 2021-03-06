## 6.4.11 Useless pattern checks

In a similar fashion, the compiler detects patterns which will never match the input value:

```haxe
switch(Leaf("foo")) {
    case Leaf(_)
       | Leaf("foo"): // This pattern is unused
    case Node(l,r):
    case _: // This pattern is unused
}
```

---

Previous section: [Exhaustiveness checks](lf-pattern-matching-exhaustiveness.md)

Next section: [String Interpolation](lf-string-interpolation.md)

Contribute: [fileAndLines](https://github.com/HaxeFoundation/HaxeManual/blob/master/06-language-features.tex#L273-273)