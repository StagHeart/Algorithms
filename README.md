# Algorithms
# My solutions to algorithm problems from leetcode.com

## First problem: 

### Longest Substring Without Repeating Characters

Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

### Answer: 
        public int lengthOfLongestSubstring(String s) {

        String builder = "";
        String longestSoFar = "";
        for(int i = 0; i < s.length(); i ++){

            String sub = s.substring(i,i+1);

            if(builder.contains(sub)){
                if(builder.length() > longestSoFar.length()){
                    longestSoFar = builder;
                }

                int subIndex = builder.indexOf(sub);
                if(subIndex != (builder.length()-1)) {
                    builder = builder.substring(subIndex+1);
                } else {
                    builder = "";
                }
            }
            builder += sub;
        }

        if(builder.length() > longestSoFar.length()){
            return builder.length();
        } else{
            return longestSoFar.length();
        }
    }
