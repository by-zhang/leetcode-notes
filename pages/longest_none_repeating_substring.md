###Approach sliding window

	int lengthOfLongestSubstring(string s) {
        int group[128] = {0};           // Storing repeated characters in an 128-bit-integer-array or an hashmap
        int len = s.size(), ans = 0;    // The values are the indices in the string.
        for (int j=0, start = 0; j<len; j++) {
            start = max(group[(int)s[j]], start); //If s[j] is repeated with s[l](obvious start<l<j), the start index will be 
            ans = max(ans, j-start+1);            // changed to l+1.
            group[(int)s[j]] = j+1;
        }
        return ans;
    }
