# Longest-String-Chain
You are given an array of words where each word consists of lowercase English letters.  wordA is a predecessor of wordB if and only if we can insert exactly one letter anywhere in wordA without changing the order of the other characters to make it equal to wordB.  

class Solution:
    def longestStrChain(self, words: List[str]) -> int:
        dp = {}  
        for word in sorted(words, key=len):
            temp = [0] 
            n = len(word)

            for i in range(n):
                if word[:i] + word[i + 1:] in dp:
                    temp.append(dp[word[:i] + word[i + 1:]])

            dp[word] = max(temp) + 1

        return max(dp.values())
