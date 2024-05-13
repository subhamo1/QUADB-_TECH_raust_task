# QUADB-_TECH_raust_task

```
** Implement a function that checks whether a given string is a palindrome or not. **

fn is_palindrome(s: &str) -> bool {
    let mut chars: Vec<char> = s.chars().collect();
    let mut rev_chars = chars.clone();
    rev_chars.reverse();
    chars == rev_chars
}


Given a sorted array of integers, implement a function that returns the index of the first occurrence of a given number.

fn find_index(nums: &[i32], target: i32) -> Option<usize> {
    for (i, &n) in nums.iter().enumerate() {
        if n == target {
            return Some(i);
        }
    }
    None
}


Given a string of words, implement a function that returns the shortest word in the string.

fn shortest_word(s: &str) -> &str {
    let mut words = s.split_whitespace();
    let mut shortest = &s;
    for word in words {
        if word.len() < shortest.len() {
            shortest = word;
        }
    }
    shortest
}

Implement a function that checks whether a given number is prime or not.

fn is_prime(n: u32) -> bool {
    if n < 2 {
        return false;
    }
    for i in 2..=(n as f64).sqrt() as u32 {
        if n % i == 0 {
            return false;
        }
    }
    true
}


Given a sorted array of integers, implement a function that returns the median of the array.

fn median(nums: &[i32]) -> f64 {
    let n = nums.len();
    if n % 2 == 0 {
        (nums[n / 2 - 1] + nums[n / 2]) as f64 / 2.0
    } else {
        nums[n / 2] as f64
    }
}

Implement a function that finds the longest common prefix of a given set of strings.

fn longest_common_prefix(strs: Vec<String>) -> String {
    if strs.is_empty() {
        return String::new();
    }
    let mut prefix = strs[0].clone();
    for s in strs.iter().skip(1) {
        prefix = common_prefix(&prefix, s);
        if prefix.is_empty() {
            break;
        }
    }
    prefix
}

fn common_prefix(s1: &str, s2: &str) -> String {
    let mut prefix = String::new();
    for (c1, c2) in s1.chars().zip(s2.chars()) {
        if c1 == c2 {
            prefix.push(c1);
        } else {
            break;
        }
    }
    prefix
}

Implement a function that returns the kth smallest element in a given array.

fn kth_smallest(nums: &mut [i32], k: usize) -> i32 {
    nums.select_nth_unstable(k - 1);
    nums[k - 1]
}

Given a binary tree, implement a function that returns the maximum depth of the tree.

use std::cell::RefCell;
use std::rc::Rc;

#[derive(Debug, PartialEq, Eq)]
struct TreeNode {
    val: i32,
    left: Option<Rc<RefCell<TreeNode>>>,
    right: Option<Rc<RefCell<TreeNode>>>,
}

fn max_depth(root: Option<Rc<RefCell<TreeNode>>>) -> i32 {
    if root.is_none() {
        return 0;
    }
    let node = root.unwrap().borrow();
    let left_depth = max_depth(node.left.clone());
    let right_depth = max_depth(node.right.clone());
    std::cmp::max(left_depth, right_depth) + 1
}


Reverse a string in Rust

fn reverse_string(s: &str) -> String {
    s.chars().rev().collect()
}

Check if a number is prime in Rust

fn is_prime(num: i32) -> bool {
    if num <= 1 {
        return false;
    }
    for i in 2..(num as f64).sqrt() as i32 + 1 {
        if num % i == 0 {
            return false;
        }
    }
    true
}


Merge two sorted arrays in Rust

fn merge_sorted_arrays(nums1: &mut Vec<i32>, m: i32, nums2: &mut Vec<i32>, n: i32) {
    let mut i = m as usize - 1;
    let mut j = n as usize - 1;
    let mut k = (m + n) as usize - 1;

    while i < m as usize && j < n as usize {
        if nums1[i] > nums2[j] {
            nums1[k] = nums1[i];
            i -= 1;
        } else {
            nums1[k] = nums2[j];
            j -= 1;
        }
        k -= 1;
    }

    while j < n as usize {
        nums1[k] = nums2[j];
        j -= 1;
        k -= 1;
    }
}


Find the maximum subarray sum in Rust do this in rust language

fn max_subarray_sum(nums: &[i32]) -> i32 {
    let mut max_sum = std::i32::MIN;
    let mut current_sum = 0;

    for &num in nums {
        current_sum = std::cmp::max(num, current_sum + num);
        max_sum = std::cmp::max(max_sum, current_sum);
    }

    max_sum
}
