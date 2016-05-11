---
title: Modified Hungarian Notation
excerpt: "My attempt to explain Hungarian notation with a touch of naming convention standard."
image: 
  feature: het-belang-van-coding-standards.jpg
  teaser: oie_11135753SRKSiEPy.jpg
  credit: wijs.be
  creditlink: https://wijs.be/nl/trends-inzichten/blog/detail/het-belang-van-coding-standards
tags: [coding standards]
comments: true
featured: true
author: Anirudha Kasralikar
date: 2016-05-08 11:27:43
modified: 2016-05-08 11:27:43
---

Coding standards define a programming style. Over the period of time its proven that following a particular standard is useful for code maintainability. In this article I am presenting introduction to modified Hungarian notation.

{% include toc.html %}

## Background  
I presume that you have basic hands-on with [PHP](http://php.net/ "PHP") programming. Also you understood how community based standard recommendation for any programming language prosper.
You can go through [PHP Standard Recommendation](http://wwference.w.php-fig.org/psr/ "PHP Standard Recommendation") as reference.

As per Wikipedia, definition of Hungarian notation is as below.

```  
Hungarian notation is an identifier naming convention in computer programming, 
in which the name of a variable or function indicates its type or intended use.   
```
 
This notation was originally invented by Charles Simonyi from Microsoft, who happens to belong to country Hungary. There are broadly 2 types of this notation.
 
### Apps Hungarian 
 
Original notation was historically called as Apps Hungarian, because this was used in Microsoft applications like Word and Excel. Developer was free to choose which prefix to use, like "rw" was used to refer to rows and "col" for columns, "ix" to mean index of an array, etc. Apps Hungarian was very useful, especially with C programming where the compiler did not provide a very useful type system.  
  
### Systems Hungarian 
  
Over the period of time there was another variant got created named Systems Hungarian, which restricts variable prefixes to limit to its actual data type, like "l" for long integer, "ul" for unsigned long, "d" for double, etc.  
 
## Modified Hungarian Notations 

Having coding standards have lot of advantages. The source code will be more comprehensive and will become easy-to-maintain.  Your code becomes your documentation.
On top of coding standards if you follow uniform variable naming standards it really adds cherry on the cake. Taking the systems hungarian notations as base, I can propose some of naming conventions as below. Add prefix to all of your variables with data type it hold. It means code not only does its job good, but is also easy to add to, maintain and debug.
I'm not proposing these as a standard, merely mentioning the thought process that goes into variable naming. 
I tried to solve following questions by proposing below convention. See examples as below.

- Are you easily able to differentiate class level variables with local variables?
- Are you able to identify primitive variables with object variables?
- Are variable names descriptive, compact and readable?.

### Local Variables

{% highlight php %}
// $int for integer
$intIntegerVariable = 100;

// $flt for float
$fltFloatVariable = 1.25;

// $dbl for double
$dblDoubleVariable = 1000000.123456;

// $str for string
$strStringVariable = "Hello World!";

// $bool for boolean
$boolBooleanVariable = true;

// $bool for all types of resources
$resResourceVariable = fopen( '/home/akasralikar/file.txt', 'r' );

// $obj for objects
$objObjectVariable = new CClassName();

// $fn for antonymous / lambda functions
$fnFunctionVariable = function( $name ) {
	printf( "Hello %s\r\n", $name );
};
{% endhighlight %}

See how function parameter names are defined with data type. 

{% highlight php %}
function doSomething( $strData ) {
	echo $strData;
}

function doSomethingElse( $objClass ) {
	echo $objClass->doSomething();
}
{% endhighlight %}

### Class Variables

{% highlight php %}
<?php

// Class Name should match with file name.
class CClassName {
	// Member Variables.
	public $m_intIntegerVariable;
	public $m_fltFloatVariable;
	public $m_dblDoubleVariable;
	public $m_strStringVariable;
	public $m_boolBooleanVariable;
	public $m_resResourceVariable;
	public $m_objObjectVariable;
	public $m_fnFunctionVariable;

	// Array Type Member Variables.
	public $m_arrintIntegerVariable;
	public $m_arrfltFloatVariable;
	public $m_arrfltDoubleVariable;
	public $m_arrstrStringVariable;
	public $m_arrboolBooleanVariable;
	public $m_arrresResourceVariable;
	public $m_arrmixMixedVariable;
	public $m_arrobjObjectVariable;
	public $m_arrfnFunctionVariable;

	// Static Member Variables.
	public static $c_intIntegerVariable;
	public static $c_fltFloatVariable;
	public static $c_fltDoubleVariable;
	public static $c_strStringVariable;
	public static $c_boolBooleanVariable;
	public static $c_resResourceVariable;
	public static $c_objObjectVariable;
	public static $c_fnFunctionVariable;

	// Static Array Type Member Variables.
	public static $c_arrintIntegerVariable;
	public static $c_arrfltFloatVariable;
	public static $c_arrfltDoubleVariable;
	public static $c_arrstrStringVariable;
	public static $c_arrboolBooleanVariable;
	public static $c_arrresResourceVariable;
	public static $c_arrmixMixedVariable;
	public static $c_arrobjObjectVariable;
	public static $c_arrfnFunctionVariable;

	public function setIntegerVariable( $intIntegerVariable ) {
		$this->m_intIntegerVariable = $intIntegerVariable;
	}

	public function setFloatVariable( $fltFloatVariable ) {
		$this->m_fltFloatVariable = $fltFloatVariable;
	}

	public function setDoubleVariable( $dblDoubleVariable ) {
		$this->m_dblDoubleVariable = $dblDoubleVariable;
	}

	public function setStringVariable( $strStringVariable ) {
		$this->m_strStringVariable = $strStringVariable;
	}

	public function setBooleanVariable( $boolBooleanVariable ) {
		$this->m_dblBooleanVariable = $boolBooleanVariable;
	}

	public function setResourceVariable( $resDoubleVariable ) {
		$this->m_resResourceVariable = $resDoubleVariable;
	}

	public function setObjectVariable( $objObjectVariable ) {
		$this->m_objObjectVariable = $objObjectVariable;
	}

	public function setFunctionVariable( $fnFunctionVariable ) {
		$this->m_fnFunctionVariable = $fnFunctionVariable;
	}

	// Similarly we can have function which accepts array type parameters and which sets array type class variables.
}

?>
{% endhighlight %}


### Conventions for naming file

In all ideal situation, its good practice to have one class ( or one trait or one interface ) per file. I propose following standard.

Start your class name with "C" and add suffix like ".class.php"

~~~
CClassName.class.php
~~~

Start your trait name with "T" and add suffix like ".trait.php"

~~~
TTraitName.trait.php
~~~

Start your interface name with "I" and add suffix like ".interface.php"

~~~
IInterfaceName.interface.php
~~~

## Conclusion

I sincerely thing coding conventions are to ease out development. This does not gurantee that your code will be rock solid. 
Its upto you to make most sense out of it as you are developer.

~~~ 
In closing, it is evident that the conventions participated in making 
the code more correct, easier to write, and easier to read. Naming conventions 
cannot guarantee good code, however; only the skill of the programmer can. 
-- Charles Simonyi ( original inventor of Apps Hungarian )  
~~~ 
