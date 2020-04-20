# Java Language

It is not possible to create generic arrays in Java because arrays are covariant (any subclass of an array can be used as its superclass) while generics are invariant.

In practice, this means the following:

'''[java]
Object objectArray[] = new Integer[10]; // it will work fine

List<Object> objectList = new ArrayList<Integer>(); // won't compile
'''
