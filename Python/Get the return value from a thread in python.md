**The function foo below returns a string 'foo'. How can I get the value 'foo' which is returned from the thread's target?**

Code example with python 3.

```python
from threading import Thread

def foo(bar):
    print('hello {}'.format(bar))
    return 'foo'

class ThreadWithReturnValue(Thread):
    def __init__(self, group=None, target=None, name=None,
                 args=(), kwargs={}, Verbose=None):
        Thread.__init__(self, group, target, name, args, kwargs)
        self._return = None
    def run(self):
        print(type(self._target))
        if self._target is not None:
            self._return = self._target(*self._args,
                                                **self._kwargs)
    def join(self, *args):
        Thread.join(self, *args)
        return self._return

new_thread = ThreadWithReturnValue(target=foo, args=('world!',))
# If there is only one parameter, the comma must be included in args

new_thread.start()
return_value = new_thread.join()
print return_value
```