---
title: "Property Declaration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology:  
  - "cpp-windows"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property keyword"
  - "declaring properties, C++"
  - "property keyword [C++]"
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Property Declaration
The way to declare a property in a managed class has changed from Managed Extensions for C++ to [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 In the Managed Extensions design, each `set` or `get` property accessor is specified as an independent method. The declaration of each method is prefixed with the `__property` keyword. The method name begins with either `set_` or `get_` followed by the actual name of the property (as visible to the user). Thus, a `Vector` providing an `x` coordinate `get` property would name it `get_x` and the user would invoke it as `x`. This naming convention and separate specification of methods actually reflects the underlying runtime implementation of the property. For example, here is our `Vector` with a set of coordinate properties:  
  
```  
public __gc __sealed class Vector {  
public:  
   __property double get_x(){ return _x; }  
   __property double get_y(){ return _y; }  
   __property double get_z(){ return _z; }  
  
   __property void set_x( double newx ){ _x = newx; }  
   __property void set_y( double newy ){ _y = newy; }  
   __property void set_z( double newz ){ _z = newz; }  
};  
```  
  
 This spreads out the functionality associated with a property and requires the user to lexically unify the associated sets and gets. Moreover, it is verbose. In the new syntax, which is more like that of C#, the `property` keyword is followed by the type of the property and its unadorned name. The `set` and `get` access methods are placed within a block following the property name. Note that unlike C#, the signature of the access method is specified. For example, here is the code example above translated into the new syntax.  
  
```  
public ref class Vector sealed {   
public:  
   property double x {  
      double get() {  
         return _x;  
      }  
  
      void set( double newx ) {  
         _x = newx;  
      }  
   } // Note: no semi-colon  
};  
```  
  
 If the access methods of the property reflect distinct access levels - such as a `public get` and a `private` or `protected set`, an explicit access label can be specified. By default, the access level of the property reflects that of the enclosing access level. For example, in the above definition of `Vector`, both the `get` and `set` methods are `public`. To make the `set` method `protected` or `private`, the definition would be revised as follows:  
  
```  
public ref class Vector sealed {   
public:  
   property double x {  
      double get() {  
         return _x;  
      }  
  
   private:  
      void set( double newx ) {  
         _x = newx;  
      }  
  
   } // note: extent of private culminates here  
  
// note: dot is a public method of Vector  
double dot( const Vector^ wv );  
  
// etc.  
};  
```  
  
 The scope of an access keyword within a property extends until either the closing brace of the property or the specification of an additional access keyword. It does not extend beyond the definition of the property to the enclosing access level within which the property is defined. In the above declaration, for example, `Vector::dot()` is a public method.  
  
 Writing the set/get properties for the three `Vector` coordinates involves three steps:  
  
1.  declare a private state member of the appropriate type.  
  
2.  return it when the user wishes to get its value.  
  
3.  assign it the new value.  
  
 In the new syntax, a shorthand property syntax is available which automates this usage pattern:  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 The interesting side effect of the shorthand property syntax is that although the backstage state member is generated by the compiler, it is not accessible within the class except through the set/get accessors.  
  
## See Also  
 [Member Declarations within a Class or Interface (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [property](../windows/property-cpp-component-extensions.md)