---
title: "Modern C++ - Data Structure [Array]"
date: "2018-12-16"
---
***
### Accessing array elements while implementing Array Data Structure 
---
#### IntArray - An integer array 

One member function of array implementation, 
eg: within class _IntArray_, element access _operator[]_ is overlaoded to return the value at _index_
```c++
 	int operator[](int index) {
    	return m_ptr[index];
  	}
```
 A call from _main()_
```c++	
	IntArray a{3};
	a[0] = 10;  // <= error 
```
gives an error: lvalue required as left operand of assignment


** This happens when you return from a function by value. A function call that returns by value is an rvalue expression,  and you cannot use an rvalue expression as the left operand of an assignment.  

But, a function call that returns by reference is an lvalue expression and will allow you to assign to it. **
We can change above function to 
 ```c++
 	int& operator[](int index) {
    	return m_ptr[index];
  	} 
 ```
which returns a reference (lvalue) to which assignment is possible.

  

#### What about a read only function using const specifier?
```c++
  	int& operator[](int index) const{
    	return m_ptr[index];
  	}
```

A statement like one below 
```c++
	a[0] = 10; 
```
will modify the content as the lvalue is now a reference and data will be modified. _const_ specifier will not have any effect.

So, always return int as value 
```c++
	int operator[](int index) const{
    	return m_ptr[index];
  	}
```


