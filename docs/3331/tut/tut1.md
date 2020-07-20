# tutorial 1 week5

1. list all delays encountered in packet switch

   * processing delay  - slightly depend
   * queuing delay
   * transmission delay - depend on size of packet
   * propagation delay

2. consider

    ```cpp
    HTTP/1.0           |          HTTP/1.1
    --------------------------------------
    non persistence         persistence
    non parallel connect    parallel connection
    ```

    answer: 8, 3

3. d

4. a

5. d

6. end-to-end delay

    ```bash
    sender ------- router -------- router -------- router ------- router

    ------- receiver
    ```

    $$
    d_{endToEnd} = d_{trans} + d_{prop} + d_{proc} + d_{queue}
    $$

7. checksum


