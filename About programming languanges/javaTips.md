1. 随机数
'''
       ArrayList<Integer> nums;
   
       public int getRandom() {
        Random random = new Random();
        return nums.get(random.nextInt(nums.size()));
    }
'''
