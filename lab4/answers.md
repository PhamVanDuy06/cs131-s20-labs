# Exercise 1
* `w01-byte` bytes/second: 689.39 byte/sec 
* `w02-byte` bytes/second: 2.31658e+06 byte/sec (~2.21 MB/sec)
* `w03-byte` bytes/second: 47628401.336932 byte/sec 

# Exercise 2

### Scenario 1:
* How many array elements can fit into a cache block? 
2 elements (Block size = 8 bytes, each int = 4 bytes)
* What combination of parameters is producing the hit rate you observe? 
Array size = 128 bytes, Block size = 8 bytes → 16 blocks cần truy cập; Step size = 1 → truy cập tuần tự; Rep count = 2 → lần thứ 2 nhiều hit
* What is our hit rate if we increase Rep Count arbitrarily? Why? 
Hit rate tăng, vì cùng các phần tử được truy cập nhiều lần, vẫn còn trong cache

### Scenario 2:
* What combination of parameters is producing the hit rate you observe? 
Array size = 128 bytes, Step size = 27 → bước nhảy xa, nhiều miss; 1 block → hit thấp
* What happens to our hit rate if we increase the number of blocks and why? 
Hit rate tăng, vì nhiều block hơn giảm việc thay thế block và lưu dữ liệu lâu hơn

### Scenario 3:
* Choose a `number of blocks` greater than `1` and determine the smallest `block size` that uses every block *and* maximizes the hit rate  
Number of blocks: 2 
Block Size: 128 bytes (phù hợp với array size, dùng mọi block, tối đa hóa hit rate)

# Exercise 3
Sắp xếp các hàm nhân ma trận từ nhanh nhất đến chậm nhất dựa trên GFlops/s:

1. jki: 0.525 GFlop/s (nhanh nhất) 
2. kji: 0.519 GFlop/s 
3. ijk: 0.466 GFlop/s 
4. jik: 0.377 GFlop/s 
5. ikj: 0.192 GFlop/s 
6. kij: 0.160 GFlop/s (chậm nhất) 

**Giải thích:** 
- Thứ tự vòng lặp ảnh hưởng đến tính cục bộ bộ nhớ (spatial & temporal locality). 
- Các thuật toán truy cập ma trận theo thứ tự cột hoặc hàng hợp lý với cách dữ liệu được lưu trong mảng 1 chiều sẽ tận dụng cache tốt hơn → GFlops cao hơn.  
- Những thuật toán có thứ tự truy cập “không tối ưu” → nhiều cache miss → GFlops thấp hơn.

