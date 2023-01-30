# Fast jsonpath-ng experiment

Fork of jsonpath-ng where I stop it from generating a new instance of yacc each
time we parse an expression. There was probably a good reason for doing this, but im not sure what.

Instantiating yacc just once speeds things up by a factor of 10 when parsing alot of expressions.

### Test code

```python
TEST = {
    "foo" : {
        "bar" : [1,2,3]
    }
}


for i in range(1000):
    expr = jp.parse("foo.bar[1]")
    v = expr.find(TEST)
```

Base speed: 5.7662 seconds

Fork speed: 0.4383 seconds







