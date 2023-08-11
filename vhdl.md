Sea la función:
$$F=\sum \lbrace 1, 2, 3, 5, 7, 11, 13 \rbrace$$
### Declaración Case

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port(
		input:   in std_logic_vector (3 downto 0) ;
		isprime: out std_logic);
end prime ;

architecture case_impl of prime is
begin
	process(input) begin--{}
		case input is
			when x"1"|x"2"|x"3"|x"5"|x"7"|x"b"|x"d"=>
			isprime <= '1';
			--when "0001" | "0010" |	"0011" |	"0101" |	"0111" |	"1011" |	"1101" |	=> isprime <= '1';
			when others =>
			isprime <= '0';
		end case;
	end process;
end case_impl;
```









```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity F2 is
    port (
        input : in std_logic_vector (3 downto 0);
        F2    : out std_logic
    );
end F2;

architecture case_impl of F2 is
begin
    process(input)
    begin
        case input is
            when
					"00010"|
					"00011"|
					"00101"|
					"00111"|
					"01011"|
					"01101"|
					"10000"|
					"10011"|
					"10101"|
					"10110"|
					"11110"
					=>
                F2 <= '1';
            when others =>
                F2 <= '0';
        end case;
    end process;
end case_impl;

```









### port map

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port{
		input:   in sts_logic_vector (3 downto O) ;
		isprime: out std_logic);
end prime ;

architecture SYN_case_impl of prime is
	
	component OAI13 is
		port( A1, B1, B2, B3: in std_Logic; Y: out std_logic);
	end component;

	component OAI12 is
		port( A1, B1, B2: in std_Logic; Y: out std_logic);
	end component;

	component INV is
		port( A: in std_Logic; Y: out std_logic);
	end component;

	component XOR2 is
		port( A, B: in std_Logic; Y: out std_logic);
	end component;

	signal n1, n2, n3, n4 : std_logic;

	begin
		U1: OAI13 port map { A1=>n2, B=>n1, B2=>input(2), B3=>input(3), Y=>isprime };
		U2: INV port map { A=>input(1), Y=>n1 };
		U3: INV port map { A=>input(3), Y=>n3 };
		U4: XOR2 port map { A=>input(2), B=>input(1), Y=>n4 };
		U5: OAI12 port map { A1=>input(0), B1=>n3, B2=>n4, Y=>n2 };
		
end SYN_case_impl;
```




![[Pasted image 20230807195139.png]]


### declaracion case?


para implementar el uso de fiboleanos "-"

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port{
		input:   in sts_logic_vector (3 downto O) ;--{}
		isprime: out std_logic);
end prime ;

architecture case_impl of prime is
begin
	process(all) begin--{}
		case? input is
			when "0--1" => isprime <= '1';
			when "0010" => isprime <= '1';
			when "1011" => isprime <= '1';
			when "1101" => isprime <= '1';
			when others => isprime <= '0';--`0`
		end case?;
	end process;
end case_impl;
```


### Declaración if
```vhdl
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port{
		input:   in sts_logic_vector (3 downto O) ;--{}
		isprime: out std_logic);
end prime ;

architecture if_impl of prime is
begin
	process(all) begin--{}
		if input = 4d"1" then isprime <= '1';
		elsif input = 4d"2" then isprime <= '1';
		elsif input = 4d"3" then isprime <= '1';
		elsif input = 4d"5" then isprime <= '1';
		elsif input = 4d"7" then isprime <= '1';
		elsif input = 4d"11" then isprime <= '1';
		elsif input = 4d"13" then isprime <= '1'
		else isprime <= '0';
		end if;
	end process;
end if_impl;
```

### Señales concurrentes

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port{
		input:   in sts_logic_vector (3 downto O) ;--{}
		isprime: out std_logic);
end prime ;

architecture logic_impl of prime is
begin
	isprime <= (input(0) AND (NOT input(3))) OR
				(input(1) AND (NOT input(2)) AND (NOT input(3))) OR
				(input(0) AND (NOT input(1)) AND input(2)) OR
				(input(0) AND input(1) AND NOT input(2));
end logic_impl;
```

### Declaración de Seleccionar

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port{
		input:   in sts_logic_vector (3 downto O) ;--{}
		isprime: out std_logic);
end prime ;

architecture selec_impl of prime is
begin
	with input select
		isprime <= '1' when 4d"1" | 4d"2" |	4d"3" |	4d"5" |	4d"7" |	4d"11" |4d"13", 
					'0' when others;
end selec_impl;
```

### Señales condicionales

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity prime is
	port{
		input:   in sts_logic_vector (3 downto O) ;--{}
		isprime: out std_logic);
end prime ;

architecture cond_impl of prime is
begin
	isprime <=
			'1' when input = 4d"1" else
			'1' when input = 4d"2" else
			'1' when input = 4d"3" else
			'1' when input = 4d"5" else
			'1' when input = 4d"7" else
			'1' when input = 4d"11" else
			'1' when input = 4d"13" else
			'0';
end cond_impl;
```


## Descripción estructural

```VHDL

```
