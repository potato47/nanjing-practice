# Day2

 **[HOME](../README.md)**

## 集合

**ArrayList：**

底层是数组实现，初始化数组大小默认是10，当数组长度不够时会新建一个更大的数组，然后将原来的数据拷贝到新的数组中，所以可以在初始化时指定大小，提高一下性能。

`ArrayList<Integer> list = new ArrayList<Integer>(1000);`

**Set去重，集合遍历：**

```java
public class ListTest {

	public static void main(String[] args) {
		//指定预估大小
		ArrayList<Integer> list = new ArrayList<Integer>(1000);
		
		list.add(1);
		list.add(2);
		list.add(3);
		list.add(3);
		
		System.out.println("list:");
		for(Integer i : list){
			System.out.println(i);
			
		}	
		
		//去重
		Set<Integer> set = new HashSet<Integer>();
		set.addAll(list);
		
		System.out.println("set:");
		for( Iterator<Integer> it = set.iterator(); it.hasNext();)
        {             
            System.out.println(it.next().toString());            
        } 
		
		//Map
		HashMap<String, String> hashMap = new HashMap<String, String>();
		hashMap.put("1", "一");
		System.out.println(hashMap.get("1"));
		for(Map.Entry<String, String> entry : hashMap.entrySet()){
			System.out.println("key:"+entry.getKey());
			System.out.println("value:"+entry.getValue());
		}
	}
}

```

