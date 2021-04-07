* ```java
  /*
  忽略测试
  
  * */
    public class IgnoreTest {
      @Test
      public void ignore1(){
          System.out.println("ignore1  执行");
      }
      @Test(enabled = false)
      public void ignore2(){
          System.out.println("ignore2 执行");
      }
    }
  ```

  总结: @Test(enabled = false)

  在注解@Test 增加(enabled = false) 就会忽略这个方法，不执行这个方法

