---
title: "Starting to Mock"
date: 2018-01-23
layout: default
---




Mock a class
Maybe mock the MAADA
Then I need to move my code into a class somewhere.

Inject a mocked class, not the real one.
```
public function __construct(SlackClient $slack)
```

When testing:

```
$slackMock = Mockery::mock(SlackClient::class)->shouldIgnoreMissing();

//use the mocked one when you new up
$notifier = new Notifier($slackMock)


```
## Laracasts


```
public function testBasicExample(0
{
  $bar = Mockery::mock('Bar');
  $bar->shouldReceive('doIt')->once()->with([])->andReturn('mocked');
  
  
  $foo = new Foo($bar);
  $output = $foo->fire();
  
  $this->assertEquals('mocked' $output);

}
```

### Newsletter Example

```
class Curl
{
  public function post()
  {
    return 'post request was made';
  }
}


class Newsletter{
  $protected $curl

  public function __construct(Curl $curl)
  {
    $this->curl = $curl;
  } 
  
  public function addToList($listName)
  {
    $data = [
    'email' => 'Foo@bar.com',
    'list' => $listName,
    ];
    
    $this->curl->post($data);
  
  }
}
```

The Test:

```
class ExampleTest extends TestCase 
{
  public function tearDown()
  {
    Mockery::close();
  }
  public function test_adds_user_to_newsletter()
  {
    //Arrange
    $curl = Mockery::mock('Curl');
    $curl->shouldReceive('post')->once()->andReturn('mocked');
    //Act
    $newsletter = new Newsletter($curl);
    $newsletter->addToList('foo-list');
    
    //Assert
  }
  

}

```

Arrange
Act
Assert




?? makePartial()

## 101

* Always add a teardown. 
```
Mockery::close;
```


## Links
https://laracasts.com/lessons/mock-that-thang


