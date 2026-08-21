test_code.c tarkoitus: 

Luoda yksinkertainen ohjelma, joka sitten muutettiin binääriksi, ja jota sitten tutkittiin.

test_code.c koodi:
#include <stdio.h>

int main() {
    printf("Hello, world!\n");
    return 0;
}

Työkaluja:

Docker Desktop, Ubuntu, GCC

Mitä tein:

Käynnistin työn dockerissa ubuntussa. Koska tässä ei ollut GCC valmiiski asenettuna, minun piti ajaa tämmöinen komento: apt install -y gcc. Tämän jälkeen laitoin tälläisen komennon: gcc test_code.c -o test_program, josta sain tälläisen: 

-rwxrwxrwx 1 root root    94 Aug 20 11:42 README.md

-rwxrwxrwx 1 root root    14 Aug 20 11:48 simpletext.md

-rwxrwxrwx 1 root root    84 Aug 20 12:49 test_code.c

-rwxr-xr-x 1 root root 15960 Aug 21 16:44 test_program

Ajoin test_program tällä komennolla: ./test_program, josta sain: Hello, world!

file test_program komennon tulokset ja selitys lyhyesti:

<img width="1682" height="89" alt="image" src="https://github.com/user-attachments/assets/b4821633-0981-41bd-b22f-787f84c1a29d" />


ELF = tiedoston tyyppi (executable file)

64-bit = Tehty 64-bittiselle 

LSB = Least Significant Byte - tavujärjestys, jota tavalliset x86-64-tietokoneet käyttävät

Lyhyt analyysi string test_program:stä

<img width="680" height="589" alt="image" src="https://github.com/user-attachments/assets/b075a7e8-fa23-4864-9d19-0462f7599f21" />


Tämä jatkuu vaikka kuinka pitkälle, mutta tässä pieni katkelma

puts = ilmeisesti GCC arvioi, että se olisi tehokkaampaa laittaa puts, eikä printf, mikä oli itse koodissa

ldd test_program lyhyesti:

<img width="1101" height="114" alt="image" src="https://github.com/user-attachments/assets/88a21eb2-0a40-4e88-a6b4-77127becc96c" />


Tarvitsee jaettua kirjastoa: libc.so.6 => /usr/lib/x86_64-linux-gnu/libc.so.6 (0x00007edb3a407000)

nm test_program lyhyesti:

<img width="409" height="36" alt="image" src="https://github.com/user-attachments/assets/dfb90b27-a772-4fe8-bc7b-e3ae5f617518" />


main() näkyy kirjaimena (T)

readelf lyhyesti:

<img width="1115" height="281" alt="image" src="https://github.com/user-attachments/assets/aba6abc9-0fec-4f4f-b035-f3965f2a65ab" />


 Class:                             ELF64
 
 Data:                              2's complement, little endian
 
 Machine:                           Advanced Micro Devices X86-64

Tekoälyn käyttö (ChatGPT):

-Auttamaan käyttämään Dockeria

-Antamaan oikeita komentoja, (file test_program, apt install -y gcc yms.)

-Selittämään, mitä kaikki erilaiset komennot tekee ja mitä kaikkea kannattaa analysoida

-Auttanut raportin suunnittelussa, mutta EI luonnissa

-Tekoäly EI ole tehnyt koodia

Lähteet:
https://www.reddit.com/r/linuxquestions/comments/17rhr8v/how_would_you_explain_the_linux_elf_format_to_a/
