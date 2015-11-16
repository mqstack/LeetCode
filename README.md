##283	Move Zeroes
	public void moveZeroes(int[] nums) {
        int j = 0;
        for(int i = 0; i < nums.length; i ++){
            if(nums[i] != 0){
                if(i != j){
                    nums[j] = nums[i];
                }
                j++;
            }
        }
        for(int i = j; i < nums.length; i ++){
            nums[i] = 0;
        }
    }
##284	Peeking Iterator
	class PeekingIterator implements Iterator<Integer> {
		private Iterator<Integer> iterator;
	
	    private Integer nextInt;
	
	    public PeekingIterator(Iterator<Integer> iterator) {
	        // initialize any member here.
	        this.iterator = iterator;
	        nextInt = iterator.next();
	    }
	
	    // Returns the next element in the iteration without advancing the iterator.
	    public Integer peek() {
	        return nextInt;
	    }
	
	    // hasNext() and next() should behave the same as in the Iterator interface.
	    // Override them if needed.
	    @Override
	    public Integer next() {
	        int thisInt = nextInt;
	        if(iterator.hasNext()){
	            nextInt = iterator.next();
	        }else{
	            nextInt = null;
	        }
	        return thisInt;
	    }
	
	    @Override
	    public boolean hasNext() {
	        if(nextInt != null){
	            return true;
	        }
	        return false;
	    }
	}

##287 Find the Duplicate Number
	public int findDuplicate(int[] nums) {
        if(nums.length > 0){
            int fast = nums[nums[0]];
            int slow = nums[0];
            while(fast != slow){
                fast = nums[nums[fast]];
                slow = nums[slow];
            }
           fast = 0;
           while(fast != slow){
               fast = nums[fast];
               slow = nums[slow];
           }
           return slow;
        }
        return -1;
    }
##289 Game of Life
	public void gameOfLife(int[][] board) {
        int m = board.length;
        int n = board[0].length;
        int [][] result = new int[m][n];
        for(int i = 0; i < m; i ++){
            for(int j = 0; j < n; j ++){

                int count = 0;
                for(int k = Math.max(i - 1, 0); k < Math.min(i + 2, m); k ++){
                    for(int l = Math.max(j - 1, 0); l < Math.min(j + 2, n); l ++){
                        if(k == i && l == j){
                            continue;
                        }
                        if(board[k][l] == 1 && result[k][l] == 0 ||
                                board[k][l] == 0 && result[k][l] == 1){
                            count ++;
                        }
                    }
                }

                if (board[i][j] == 1) {
                    if ((count < 2 || count > 3)) {
                        board[i][j] = 0;
                        result[i][j] = 1;
                    }
                    if ((count == 2 || count == 3)) {
                        result[i][j] = 0;
                    }
                } else if (count == 3) {
                    board[i][j] = 1;
                    result[i][j] = 1;
                } else {
                    result[i][j] = 0;
                }
                
            }
        }
    }
##290 World Pattern

	public static boolean wordPattern(String pattern, String str) {
        if(pattern == null || str == null) {
            return false;
        }

        char array[] = pattern.toCharArray();
        String strs[] = str.split(" ");

        if(array.length != strs.length){
            return false;
        }

        HashMap<Character, String> map = new HashMap<>();
        for(int i = 0; i < array.length; i ++){
            if(map.containsValue(strs[i]) && !map.containsKey(array[i])){
                return false;
            }
            if(!map.keySet().contains(array[i])){
                map.put(array[i], strs[i]);
            }

            if(!map.get(array[i]).equals(strs[i])){
                return false;
            }
        }
        return true;
    }
##292	Nim Game
    public boolean canWinNim(int n) {
	    while(n > 4){
	        n = n - 4;
	    }
	    if(n < 4){
	        return true;
	    }else{
	        return false;
	    }
    }

