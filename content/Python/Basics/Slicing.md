It is a way of splitting a list or a tuple.

```python
list = [a,b,c,d,e,f]
print(list[2:5]) ## will print c,d,e
```

First included, second excluded.



**To go to the end without specifying a stop**:
`print(list[2:])`

Just don't write the second number
.

You can do the same with the starting number as well.


### Increments
In order to have a set an increment, you can write like:
`list[2:5:2]` which will print 'c,e'

For getting every second item:
```
list[::2]
```


- If you specify -1 as the increment, it will reverse the list.