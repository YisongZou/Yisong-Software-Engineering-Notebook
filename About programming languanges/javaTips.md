1. 随机数
```
random.nextInt(Interger int);

Eg:
       ArrayList<Integer> nums;
   
       public int getRandom() {
        Random random = new Random();
        return nums.get(random.nextInt(nums.size()));
    }
```

