---
layout: default
title: "Laravel Testing"
date: 2017-08-11
---
```
$this->click('Click Me');

```

### Unit Testing
Zoomed in.

Unit and Acceptance/Functional folders.

Can trigger tests just on one folder.

** extend PHPUnit_Framework_TestCase **

* assertEquals
* assertTrue


```
public function test_product_has_a_name
{

  $product = new Product('Fallout 4');

  $this->assertEquals($product->name,'Fallout 4');
}

```  

** DRY **
```

protected $product;

public function setUp()
{
  $this->product = new Product('Fallout 4',59);

}
```

## More Unit Testing

Just testing that functions work.

assertCount

## Testing Eloquent

Integration Testing

Now need to extend TestCase because we are using Laravel.


```
function it_fetches_trending_articles
{
  // Given - set up the world
  
  //use ModelFactory - can create more than one
  factory(Article::class,3)->create
  
  // When
  
  $articles = Article::trending();
  
  // Then
  
  $this->assertEquals($mostPopular->id, $articles->first()->id);
  
}


```
Every test should assume the same world, so don't keep adding to the db.

```use DatabaseTransactions```

This will begin and rollback! 

** Scopes **

## A Testing Database Connection

## Testing Collabarators

```
$this->setExpectedException('Exception')


```

Maybe I can use ```instanteof()``` in my factories.


## Homework Solutions


## Regression Testing

Adding new tests after bugs found in testing.
1, Write test for bug.
2, Fix bug.
3, Test will pass.




## Liking a Model with TDD

## Test Method Refactoring

## Design A Fluent API with TDD

## Testing Email With Custom Assertions

## PHPUnit Prophecies

## Bug Fixing Workflow













