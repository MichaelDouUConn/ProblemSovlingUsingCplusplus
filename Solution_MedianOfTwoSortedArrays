class Solution {
public:
    void reduceSortedArrays(vector<int>& v1, int& start1, int& end1, vector<int>& v2, int& start2, int& end2, int& count, int L){
        int mid1 = 0;
        int len1 = 0;
        int mid2 = 0;
        int len2 = 0;
        if (start1 == end1 && start2 == end2){
            mid1 = start1;
            len1 = 1;
            mid2 = start2;
            len2 = 1;
        }
        else if (start1 == end1 && start2 < end2){
            mid1 = start1;
            len1 = 1;
            len2 = L;
            mid2 = start2+len2-1;
        } else if (start1 < end1 && start2 == end2){
            mid2 = start2;
            len2 = 1;
            len1 = L;
            mid1 = start1+len1-1;
        } else {
            mid1 = (start1+end1)/2;
            len1 = mid1-start1+1;
            len2 = L - len1;
            mid2 = start2+len2-1;
        }
        if(v1.at(mid1) < v2.at(mid2)){
            count += len1;
            start1 = mid1+1;
            end2 = mid2;
            
        } else {
            count += len2;
            start2 = mid2+1;
            end1 = mid1;
        }                
    }
    
    double findTargetNumber(vector<int>& nums1, vector<int>& nums2, int target){
        int m = nums1.size();
        int n = nums2.size();            
            int start1 = 0;
            int end1 = m-1;
            int start2 = 0;
            int end2 = n-1;            
            int count = 0;
           
            while( (start1<=end1) && (start2<=end2) ){
                if (target-count == 1){
                    return min(nums1.at(start1),nums2.at(start2));
                }
                reduceSortedArrays(nums1, start1, end1, nums2, start2, end2, count, target-count);
            }
            
            if (start1>end1){
                return nums2.at(start2+target-count-1);                
            } else {
                return nums1.at(start1+target-count-1);
            }        
            
    }
    
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int m = nums1.size();
        int n = nums2.size();
        if ( (m+n)%2 != 0 ){
            return findTargetNumber(nums1, nums2, (m+n+1)/2);            
        } else {
            return (findTargetNumber(nums1, nums2, (m+n)/2) + findTargetNumber(nums1, nums2, (m+n)/2+1))/2;
        }        
    }
};

