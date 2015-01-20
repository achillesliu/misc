# for loop and list
I have about 5 hunred books, and want to get some of their properties then compare them. The long program confused me on whether list of dict I should use. So I write them down here to give a clear thought.

```python
lst = list()
for book in books:
    # get some properties in the book
    dict = book.properties
    lst.append(dict)
```

That is so easy! 
1. List definition before the list
2. Properties are turned into dict
3. Then the dict is appended to the list

If I have more hierachy level to compute, just make a iteration.
So easy!
