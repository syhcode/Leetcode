## Q93[Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/) 

### Solution 1 Backtracking
#### Idea:
Judging the last one of 4 sections, if it is valid we get a valid result,or backtrack.
Backtracking depends on a List<Integer> storing the temporary valid first 3 IP sections.
#### Time Complexity: 
O(1)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<String> restoreIpAddresses(String s) {
        List<String> result = new ArrayList<String>();
        List<Integer> list = new ArrayList<Integer>();
        dfs(s,result,list,0,4);
        return result;
    }
    public void dfs(String s, List<String> result, List<Integer> list, int index, int remain){
        if(remain==1){
            String cur = s.substring(index,s.length());
            if(!isValid(cur)){
                return;
            }
            int tmp = Integer.parseInt(cur);
            String str = "";
            for(int i:list){
                str+=i+".";
            }
            str+=tmp;
            result.add(str);
        }else{
            // do the first 3 sections
            for(int i=1;i<4;i++){
                int end = index+i;
                if(end>=s.length()){
                    //leave "remain==1" to process
                    break;
                }
                String cur = s.substring(index,end);
                if(!isValid(cur)){
                    continue;
                }
                // got a valid section of first 3 sections.
                int tmp = Integer.parseInt(cur);
                list.add(tmp);
                dfs(s,result,list,end,remain-1);
                
                //backtracking
                list.remove(list.size()-1);

            }
        }
    }
    public boolean isValid(String s) {
        if (s.length() > 3 || s.length() == 0)
            return false;
        if (s.length() > 1 && s.charAt(0) == '0')
            return false;
        if (s.length() == 3 && Integer.parseInt(s) > 255)
            return false;
        return true;
    }
}
 
```
#### Reference:

---

