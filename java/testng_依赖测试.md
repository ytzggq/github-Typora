```java
public class DependTest {
    @Test
    public void test1(){
        System.out.println("test1 run");
    }
    @Test(dependsOnMethods = "test1")
    public void test2(){
        System.out.println("test2 run");
    }
}

```

依赖测试：

也就是test2方法依赖test1方法；test1方法