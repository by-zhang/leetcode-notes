### approach #1 (Two-pass Hash Table)
    class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            vector<int> res;
            if (nums.size() >= 2) {
                map<int, int> hmap;
                for (unsigned int i=0; i<nums.size(); i++) {
                    hmap.insert(pair<int, int>(nums[i], i));
                }
                unsigned int j;
                for (unsigned int i=0; i<nums.size(); i++) {
                    int temp = target - nums[i];
                    if( hmap.count(temp) ) {
                        j = hmap[temp];
                        if ( j < i ) {         ## if j>i, cannot pass the case <[3,3] , 6>
                            res.push_back(i);  ## cuz keys in a map is not replicable
                            res.push_back(j);  ## time complexity:O(n) We traverse the list with n elements twice
                        }                      ## and O(1) for looking up an element in the hash table
                    }                          ## space complexity:O(n)
                }
            }
            return res;
        }
    };