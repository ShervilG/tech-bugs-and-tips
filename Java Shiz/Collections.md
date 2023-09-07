#java #collection

# Set, HashSet and Maps
- Don't use arrays as keys since the hashCode can be different for similar objects, use a **List** instead
# Generics
``` Java 
// We wont be able to add anything to this list, only use as method param
List<? extends B> list;

// To add to list we need to create it like this
List<? super B> list;
```
