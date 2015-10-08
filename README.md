#290 World Pattern

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

