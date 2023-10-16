# Digital Logic with TL-Verilog and Makerchip
### Combinational logic in TL-Verilog using Makerchip 

<details>
<summary>Introduction To Logic Gates</summary>

**Logic Gates**
![Screenshot from 2023-10-12 20-35-00](https://github.com/JBavitha/bavitha_riscv/assets/142578450/f47abbd6-0c83-4225-a175-fcf4f22f9003)

**Combinational Circuit**
![Screenshot from 2023-10-12 20-39-10](https://github.com/JBavitha/bavitha_riscv/assets/142578450/492f2cea-7577-45ab-9644-e0994e29fa87)


**Adder**
![Screenshot from 2023-10-12 20-40-23](https://github.com/JBavitha/bavitha_riscv/assets/142578450/46500938-769b-4f69-9b5a-01d73f17d305)

**Boolean Operators**
![Screenshot from 2023-10-12 20-51-08](https://github.com/JBavitha/bavitha_riscv/assets/142578450/c1a093fb-9cf5-41c3-803c-c42199f0b1b5)

</details>



<details>
<summary>Basic Mux Implementation And Introduction To Makerchip </summary>

**Mux**
![Screenshot from 2023-10-15 13-30-49](https://github.com/JBavitha/bavitha_riscv/assets/142578450/1abcea7b-12d8-401b-82d4-e1fe20c6de8a)

**Chaining Ternary Operator**
![Screenshot from 2023-10-15 13-48-31](https://github.com/JBavitha/bavitha_riscv/assets/142578450/498fe737-669b-437f-b4d1-045ce8eabcce)

**Makerchip**
![Screenshot from 2023-10-15 13-56-29](https://github.com/JBavitha/bavitha_riscv/assets/142578450/66879614-1a30-4065-9c92-aaa2310e37fd)

![Screenshot from 2023-10-15 14-24-42](https://github.com/JBavitha/bavitha_riscv/assets/142578450/5560388d-40f6-40a7-a46c-766997600188)



</details>

<details>

<summary>Labs For Combinational Logic </summary>

![Screenshot from 2023-10-15 14-39-03](https://github.com/JBavitha/bavitha_riscv/assets/142578450/dbe58180-2671-4add-9c31-066ff48e92d3)


- Inverter

![Screenshot from 2023-10-15 14-52-02](https://github.com/JBavitha/bavitha_riscv/assets/142578450/ac2acdb3-ebcf-48e6-8cf2-8bc4c142d1b4)

- AND gate

![Screenshot from 2023-10-15 15-08-42](https://github.com/JBavitha/bavitha_riscv/assets/142578450/32bbd58e-9c30-4f9f-9277-14197c61c27f)


- Arithmetic Operations (using vectors)


![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/548d491d-d55f-4b49-8bc9-6d5787d87f34)

- Multiplexer
'''$out  = $sel ? $in1: $in2'''

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/afd008ec-089d-426a-879b-c4367b41e283)

'''$out[7:0]  = $sel ? $in1[7:0]: $in2[7:0]'''

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/c51825ee-d564-4c2c-9189-5c45272e6deb)



</details>


### Sequential Logic
<details>

<summary>Introduction To Sequential Logic And Counter Lab </summary>  

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/df2930bf-71c3-414f-9271-83e74e1cbe78)

- Sequential Logic is sequenced by a clock signal
- D-flipflop
  - Q Output: This is the main output of the flip-flop and represents the state of the D input at the last clock edge. It reflects the data stored in the flip-flop.
  - Q' (Q-bar) Output: This is the complement of the Q output. If Q is 1, then Q' is 0, and vice versa.
  - The D flip-flop also has a Reset input that can be used to reset the flip-flop to a specific state.

- The whole circuit can be viewed as bid state machine
![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/750313d2-028b-4dd4-ae50-b5f8a0bbe017)

#### Fibonacci series

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/077cdf73-1ab8-4999-bd09-37601d8b5267)

- Reset

```$val[15:0] = $reset ? 1 : >>1$val + >>2$val```

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/d37dfbfb-7515-4dc0-8fd3-fc32240ba6e8)

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/5756cbf7-6c3d-421a-957d-917c14d45238)


#### Free running counter

```
$cnt[31:0] = $reset ? 0 : (1 + >>1$cnt);
```

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/81626fef-c234-45c9-b244-e825bf7c1191)




</details>

<details>

<summary>Sequential Calculator Lab </summary>

#### Values in verilog 

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/64e8eae5-1aeb-404f-9af3-21102502f404)

- '0: All Os (width based on context).
- 'X: All DONT-CARE bits.
- 16'd5: 16-bit decimal 5.
- 5'b00XX1: 5-bit value with DONT-CARE bits.
- 1: 32-bit (signed) 1.

- Our simulator configuration:
  - will zero-extend or truncate when widths are mismatched (without warning)
  - uses 2-state simulation (no X's)

  
**Sequential Calculator**

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/1cce9dfd-0c52-425c-871c-b50882ba3c02)


</details>

<details>

<summary></summary>

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/5e7d1e6c-df53-42cd-afa5-043c124ef9c6)

**TL Verilog**
```
|calc
         @1
            $aa_sq[7:0] = $aa[3:0] ** 2;
            $bb_sq[7:0] = $bb[3:0] ** 2;
         @2
            $cc_sq[8:0] = $aa_sq + $bb_sq;
         @3
            $cc[4:0] = sqrt($cc_sq);

```
**Retiming**
```
|calc
         @0
            $aa_sq[7:0] = $aa[3:0] ** 2;
         @1 
            $bb_sq[7:0] = $bb[3:0] ** 2;
         @2
            $cc_sq[8:0] = $aa_sq + $bb_sq;
         @4
            $cc[4:0] = sqrt($cc_sq);

```














  
</details>





**Implementation Plan**

![image](https://github.com/JBavitha/bavitha_riscv/assets/142578450/957504ac-1cfe-4eb5-83b3-688634aa647b)

























