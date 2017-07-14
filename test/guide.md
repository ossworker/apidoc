# Vuep 使用

?> 1111

!> 2222

```java

  public class Demo{
    public void test01(){
      System.out.println("----");
    }
  }

```

<vuep template="#example"></vuep>

<script v-pre type="text/x-template" id="example">
  <template>
    <div>Hello, {{ name }}!</div>
  </template>

  <script>
    module.exports = {
      data: function () {
        return { name: 'Vue' }
      }
    }
  </script>
</script>

<vuep template="#example1"></vuep>
<script v-pre type="text/x-template" id="example1">
  <template>
    <div>您好, {{ name }}!</div>
  </template>

  <script>
    module.exports = {
      data: function () {
        return { name: 'Vue' }
      }
    }
  </script>
</script>

## 111
### 测试1
### 测试2


## 222
### demo1
### demo2

