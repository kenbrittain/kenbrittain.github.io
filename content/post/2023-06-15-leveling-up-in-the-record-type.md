---
title: Leveling Up in the Record Type
date: 2023-06-15
postindex: 67
url: /post/67/leveling-up-in-the-record-type
---

The record type was introduced in C# 9.0 and released in November of 2020. I saw the announcements but ignored them. That makes it only took three (3) years since its introduction for me take a look.

I ignored the record type because I thought it was a syntactic sugar feature. Something cute that would be used to save some time by having the compiler generate some code. It turns out, that is exactly what this feature is.

```csharp
public record Customer(string Name, string Address);
```

The compiler will generate public properties for the named properties of the record. It will also create the `Equals()`, `GetHasCode()`, and `ToString()` methods.

```csharp
// Private constructor
private Customer(string name, string address) {
    Name = name;
    Address = address;
}

// Public properties
public string Name { get; }
public string Address { get; }

// Equals() method
public override bool Equals(object obj) {
    if (obj == null) {
        return false;
    }
    if (obj.GetType() != this.GetType()) {
        return false;
    }
    Customer other = (Customer)obj;
    return Name == other.Name && Address == other.Address;
}

// GetHashCode() method
public override int GetHashCode() {
    return Name.GetHashCode() * 13 + Address.GetHashCode();
}

// ToString() method
public override string ToString() {
    return $"Customer {{ Name = {Name}, Address = {Address} }}";
}
```

You can add additional methods yourself because this is only masking the compiler generated class. There is no magic with the record type. Only a simpler syntax.

I found the record type to come up short when using serialization. If you need to apply an attribute to any of the fields then you need to write the field itself as a property. This removes a big promise of this feature.

The record seems a helpful feature when using for simple data classes. I can see it taking over for the data transfer objects of yesteryear.

Just don't serialize them without properly naming your fields. At this point you will probably just be writing a class anyway.
