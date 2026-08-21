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

Koko oli noin 16KB

ELF = tiedoston tyyppi (executable file)

64-bit = Tehty 64-bittiselle 

LSB = Least Significant Byte - tavujärjestys, jota tavalliset x86-64-tietokoneet käyttävät

Lyhyt analyysi string test_program:stä

puts = ilmeisesti GCC arvioi, että se olisi tehokkaampaa laittaa puts, eikä printf, mikä oli itse koodissa

ldd test_program lyhyesti:

Tarvitsee jaettua kirjastoa: libc.so.6 => /usr/lib/x86_64-linux-gnu/libc.so.6 (0x00007edb3a407000)

nm test_program lyhyesti:

main() näkyy kirjaimena (T)

readelf lyhyesti:

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
