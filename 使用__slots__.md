使用`__slots__`

python是动态语言，我们可以给实绑定任何属性和方法

```python
class Student(object):
    pass
>>> def set_age(self, age): # 定义一个函数作为实例方法
...     self.age = age
...
>>> from types import MethodType
>>> s.set_age = MethodType(set_age, s) # 给实例绑定一个方法(但该方法只属于实例s)
>>> s.set_age(25) # 调用实例方法
>>> s.age # 测试结果
#给所有实例绑定方法
>>> def set_score(self, score):
...     self.score = score
...
>>> Student.set_score = set_score



综上，因为python是动态语言，所以我们可以给实例绑定属性和方法
但是，要对实例的属性进行限制，比如只能对Student的实例添加 name 和 age 属性
class Student(object):
    __slots__ = ('name','age')

    
#__slots__仅对当前类的实例其作用，对其继承的子类是不起作用的
class GraduateStudent(Student):
    pass
g = GraduateStudent()
g.score = 100
#这里在Student的子类GraduateStudent添加score属性

```



