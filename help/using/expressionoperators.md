---
title: Operators
seo-title: Operators
description: Operators
seo-description: Learn about operators in journeys' advanced conditions
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: journeys
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: n
internal: n
snippet: y
---


# Operators {#concept_wd5_pj5_dgb}

There are two kinds of operators: unary operators and binary operators. There are left-hand unary operators and right-hand unary operators.

    ```

    // left-hand unary operators
    &lt;operator> &lt;operand> // operand is an expression
    not (@{LobbyBeacon.endUserIDs._experience.emailid.id}=="example@adobe.com")

    // right-hand unary operators
    &lt;operand> &lt;operator> // operand is an expression
    @{LobbyBeacon.endUserIDs._experience.emailid.id} is not null

    // binary operators
    &lt;operand1> &lt;operator> &lt;operand2>
    (@{LobbyBeacon.endUserIDs._experience.emailid.id}=="example1@adobe.com") or
    (@{LobbyBeacon.endUserIDs._experience.emailid.id}=="example2@adobe.com")
    ```

Here is the list of supported operators:

|Category|Operator|Literal Expression &nbsp; &nbsp; &nbsp; &nbsp;|Example|
|--- |---|:-------------:|:----------:|
|Logical|and|<ul><li>`<expression1> and <expression2>`</li><li>Both `<expression1>` and `<expression2>` must be boolean.</li><li> The result is boolean.</li></ul>|`3.14 > 2 and 3.15 < 1`|
|Logical|or|<ul><li>`<expression1> or <expression2>`</li><li>Both `<expression1> and <expression2>` must be boolean.</li><li> The result is boolean.</li></ul>|3.14 > 2 or 3.15 < 1|
|Logical|not|<ul><li>`not <expression>``<expression>` must be boolean.</li><li> The result is boolean.</li></ul>|not 3.15 < 1|
|Comparison|is null|<ul><li>`<expression> is null`</li><li>The result is boolean.</li><li>Note that null means the expression has no evaluated value.</li></ul>|`@{BarBeacon.location} is null`|
|Comparison|is not null|<ul><li>`<expression> is not null`</li><li>The result is boolean.</li><li>Note that null means the expression has no evaluated value.</li></ul>|@{BarBeacon.location} is not null|
|Comparison|has null|<ul><li>`<expression> has null``<expression>` must be a list.</li><li>The result is boolean.</li><li>Useful to identify that a list contains at least one null value.</li></ul>|`["foo", "bar", null] has null`returns true`["foo", "bar", ""] has null`returns false because "" is not considered as null.|
|Comparison|==|<ul><li>`<expression1> == <expression2>`</li><li>Both `<expression1>` and `<expression2>` must have the same data type.</li><li> The result is boolean.</li></ul>|`3.14 == 42``"foo" == "bar"`|
|Comparison|!=|<ul><li>`<expression1> != <expression2>`</li><li> Both `<expression1>` and `<expression2>` must have the same data type.</li><li> The result is boolean.</li></ul>|`3.14 != 42``"foo" != "bar"`|
|Comparison|>|<ul><li>`<expression1> > <expression2>`</li><li>Datetime can be compared with Datetime.</li><li>Datetimeonly can be compared with Datetimeonly.</li><li>Both integer or decimal can be compared with both integer or decimal.</li><li>Any other combination is forbidden.</li><li>The result is boolean.</li></ul>|3.14 > 42|
|Comparison|>=|<ul><li>`<expression1> >= <expression2>`</li><li>Datetime can be compared with Datetime.</li><li>Datetimeonly can be compared with Datetimeonly.</li><li>Both integer or decimal can be compared with both integer or decimal.</li><li>Any other combination is forbidden.</li><li>The result is boolean.</li></ul>|42 >= 3.14|
|Comparison|<|<ul><li>`<expression1> < <expression2>`</li><li>Datetime can be compared with Datetime.</li><li>Datetimeonly can be compared with Datetimeonly.</li><li>Both integer or decimal can be compared with both integer or decimal.</li><li>Any other combination is forbidden.</li><li>The result is boolean.</li></ul>|42 < 3.14|
|Comparison|<=|<ul><li>`<expression1> <= <expression2>`</li><li>Datetime can be compared with Datetime.</li><li>Datetimeonly can be compared with Datetimeonly.</li><li>Both integer or decimal can be compared with both integer or decimal.</li><li>Any other combination is forbidden.</li><li>The result is boolean.</li></ul>|42 <= 3.14|
|Arithmetic|+|<ul><li>`<expression1> + <expression2>` </li><li>Both expressions must be numeric (integer or decimal). </li><li>The result is also numeric.</li></ul>|`1 + 2`<br/>Returns 3|
|Arithmetic|-|<ul><li>`<expression1> - <expression2>`</li><li> Both expressions must be numeric (integer or decimal).</li><li> The result is also numeric.</li></ul>|`2 - 1`<br/>Returns 1|
|Arithmetic|/|<ul><li>`<expression1> / <expression2>` </li><li>Both expressions must be numeric (integer or decimal). </li><li>The result is also numeric.</li><li> `<expression2>` must not be equal to 0 (returns 0).</li></ul>|`4 / 2`<br/>Returns 2|
|Arithmetic|*|<ul><li>`<expression1> * <expression2>`</li><li> Both expressions must be numeric (integer or decimal). </li><li>The result is also numeric.</li></ul>|`3 * 4`<br/>Returns 12|
|Arithmetic|%|<ul><li>`<expression1> % <expression2>` </li><li>Both expressions must be numeric (integer or decimal).</li><li> The result is also numeric</li></ul>.|`3 % 2`<br/>Returns 1|
|Math|is numeric|<ul><li>`<expression> is numeric`</li><li>The type of the expression is integer or decimal.</li></ul>|@{BarBeacon.location} is numeric.|
|Math|is integer|<ul><li>`<expression> is integer`</li><li>The type of the expression is integer.</li></ul>|@{BarBeacon.location} is integer|
|Math|is decimal|<ul><li>`<expression> is decimal`</li><li>The type of the expression is decimal.</li></ul>|@{BarBeacon.location} is decimal|
|String|+|<ul><li>`<string> + <expression>`</li><li>`<expression> + <string>`</li><li>It concatenates two expressions or more. </li><li>The first expression must be a string.</li><li> The other expressions can be of any type.</li><li> The result is a string.</li></ul>|`"the current time is " + (now()) Returns  "the current time is 2019-09-23T09:30:06.693Z"`(now()) + " is the current time"Returns 2019-09-23T09:30:06.693Z is the current time`"a" + "b" + "c" + 1234 Returns abc1234|
|Date|+|<ul><li>`<expression + <duration>`</li><li>Append a duration to a dateTime, a dateTimeOnly or a duration.</li></ul>|`toDateTime("2011-12-03T15:15:30Z") + toDuration("PT15M")`<br/>Returns 2011-12-03T15:30:30Z<br/>`toDateTimeOnly("2011-12-03T15:15:30") + toDuration("PT15M")`<br/>Returns 2011-12-03T15:30:30<br/>`now() + toDuration("PT1H")`<br/>Returns a dateTime (with UTC timezone) one hour later from current time<br/>`toDuration("PT1H") + toDuration("PT1H")`<br/>Returns returns PT2H|