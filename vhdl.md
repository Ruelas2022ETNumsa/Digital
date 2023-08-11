Sea la función:
$$F=\sum \lbrace 2, 3, 5, 7, 11, 13, 16, 19, 21, 22, 30 \rbrace$$
### Declaración Case

```VHDL
library IEEE;
use IEEE.std_logic_1164.all;

entity EJ_f_2 is
	port(
		input:   in std_logic_vector (7 downto 0) ;
		F: out std_logic);
end EJ_f_2 ;

architecture case_impl of prime is
begin
	process(input) begin
		case input is
			when
				x"02"|// para hexadecimales
				x"03"|
				x"05"|
				x"07"|
				x"0b"|
				x"0d"|
				x"10"|
				x"13"|
				x"15"|
				x"16"|
				x"1e"
				=>
			F <= '1';
			when others =>
			F <= '0';
		end case;
	end process;
end case_impl;
```

