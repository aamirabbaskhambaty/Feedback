### Feedback Questions

1. Which parts of the lab specification have you found most confusing or difficult to understand?

Ans:
The confusing part of this lab has been the pio logic analyzer example and its modifciation to read the i2c signal.
To understand the flow of the whole code has been confusing for me.
To begin with i found it diffciult to understand the following funtions clearly:
a. 
```
void logic_analyser_init(PIO pio, uint sm, uint pin_base, uint pin_count, float div)
```
b. 
```
void logic_analyser_arm(PIO pio, uint sm, uint dma_chan, uint32_t *capture_buf, size_t capture_size_words,
                        uint trigger_pin, bool trigger_level)
```
c. It has also been difficult to understand the DMA Transfer code as well:
```
dma_channel_config c = dma_channel_get_default_config(dma_chan);
    channel_config_set_read_increment(&c, false);
    channel_config_set_write_increment(&c, true);
    channel_config_set_dreq(&c, pio_get_dreq(pio, sm, false));

    dma_channel_configure(dma_chan, &c,
        capture_buf,        // Destination pointer
        &pio->rxf[sm],      // Source pointer
        capture_size_words, // Number of transfers
        true                // Start immediately
    );
```
Thus in order to understand these functions and then modify the underlying example to read the i2c traffic from the sensor has been challenging.


2. Which lab topics have you found most confusing or difficult to understand?
Fully understanding and implementing the Pio to its full capacity has been diffciult to understand.
a. Understand parts of the .pio file, such as the wrap.target was particularly difficult.
b. This posed a huge impediment to modify and optimize the current pio file in the logic analyzer example to read the i2c traffic.

3. Which parts of the lab have you found most difficult to implement?
As stated in the previous question implementing pio from scratch has been challenging for me.
While i treid my best to understand the pio implementation including the C-SDK function as well as the assembly language instructions 
it has been challenging to impolement and mofiy the file for my own use cases, for example creating a new pio program to read inputs in which i found a difficult time tackling the following:
a. Understanding the wrap target and modifcying it to read inputs using pio.
b. initialization and configuring the state machines, pio instances and adding the gpios.
c. Reading data from the FIFO.
d. Decinidng the right clock division factor.

4. What steps have you taken to resolve these difficulties? Any other barriers you have faced to completing this assignment?
a. I referred to the C-SDK examples to find any references to PIO.
b. I also referred to online vidoes, blogs and tutorials especially of Shawn Hymel.
c. Student Repositories.
