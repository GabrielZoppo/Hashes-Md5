# Códigos Python:
 * Código Para transformar strings em hash 
 
 ~~~Python
 # declarando a biblioteca necessária
 import hashlib

# fazendo uma função para transformar a string em hash MD5
def main(): 

    text = "dado"
    textUtf8 = text.encode("utf-8")

    hash = hashlib.md5( textUtf8 )
    hexa = hash.hexdigest()
   
    print ( hexa )

    return
    
# chamando a função
main()
 ~~~
 * Código para quebrar hash usando força bruta:
 
 ~~~Python
 # importando as bibliotecas necessárias para a quebra das hashes
import hashlib
from threading import Thread

# declarando as hashes a serem quebradas
hashes = [
"59275c0a57c1912eba3b237d2bc57d6c",
"0978496b93e1071dc7c40a81e95c3925",
"742e6fde3ea050e413ee491f0290354a",
"07208f17a430a235ceefc8a856b57f56",
"42c76757ae2b89a1ae9e7d3f2f918aac",
"c1491ad8c03e2ada58d3e7d773041723",
"50aea0edbb9c8b91a810ad7f2e90b568",
"dd1df27fef89eb9b0364c3803fcf4ceb",
"8b365f0fd77f4a8b29b22fa9b3f46d2c",
"5c281ef353b00703e224fae631403440",
"6eba2afd08b788a46def38c420580240",
"eb9b0daccbff5f6be60d241263720955",
"82c8a24e125df09ce18906eda3e25062",
"5c281ef353b00703e224fae631403440",
"6eba2afd08b788a46def38c420580240",
]
hashes1 = [
"eb9b0daccbff5f6be60d241263720955",
"82c8a24e125df09ce18906eda3e25062",
"751c39690fb8071c7292776d7b6a638f",
"6c066f396461ba8831088bcf8c2e8c19",
"b5197cebb685d19c1ffab146e9125783",
"f649f3c248152f0e43638ac6cbc06594",
"47cb7cc4c1d3c8a0eb2afb5f9ce64377",
"95650081a595315bd36c2801f2c120af",
"c5dd4880f4aa1d623f28651afec2ed4a",
"c46901272edfbe7730df9ff09518edb2",
"8215e46a79498744224eb239cf100dc2",
"c5781aa76d4e4315f09f1c2c5afa04a8",
"8d9a372b47cf443cac9f097420538f05",
"61650746431e6c31ae845520b2a69ea2",
"d69e23084c0be871c5f95ed2ead45ffc",
"f8e15734344f8bdd5026fa1852b89487",
"04b78196fdc6ffe443618571deb25846",
"a7af447f4133a73d3418fda6e650fcd3",
"29733d63917ebcda6c88ba69da1b25a2"
]

# declarando a lista de possiveis caracteres para fazer a quebra das hashes
characters = list("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%&*()_-+=[]{?}/\\|><")

characters1 = list("rstuvwxyz0123456789!@#$%&*()_-+=[]{?}/\\|><")

characters2 = list("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopq")

out = open("./saida.txt","w") # cria um arquivo para armazenar as chaves descriptografadas 

# definindo um metodo para quebra de hash MD5
def brute_force1():
# for para fazer a quebra de cada um dos possiveis 7 caracteres
    for p7 in characters1:
        for p6 in characters:
            for p5 in characters:
                for p4 in characters:
                    for p3 in characters:
                        for p2 in characters:
                            for p1 in characters:
                                
                                # um if para quando a hash for de 5 caracteres
                                palavra5 = "%s%s%s%s%s"%(p5,p4,p3,p2,p1)
                                hash5 = (hashlib.md5(palavra5.encode())).hexdigest()

                                if hash5 in hashes:
                                    out = open("./saida.txt","a")
                                    resultado = hash5 + "," + palavra5 + "\n"
                                    print(resultado)
                                    out.write(resultado)
                                    out.close()
                                
                                # um if para quando a hash for de 6 caracteres
                                palavra6 = "%s%s%s%s%s%s"%(p6,p5,p4,p3,p2,p1)
                                hash6 = (hashlib.md5(palavra6.encode())).hexdigest()

                                if hash6 in hashes:
                                    out = open("./saida.txt","a")
                                    resultado = hash6 + "," + palavra6 + "\n"
                                    print(resultado)
                                    out.write(resultado)
                                    out.close()
                                
                                # um if para quando a hash for de 7 caracteres
                                palavra7 = "%s%s%s%s%s%s%s"%(p7,p6,p5,p4,p3,p2,p1)
                                hash7 = (hashlib.md5(palavra7.encode())).hexdigest()

                                if hash7 in hashes:
                                    out = open("./saida.txt","a") 
                                    resultado = hash7 + "," + palavra7 + "\n"
                                    print(resultado)
                                    out.write(resultado)
                                    out.close()

# definindo um metodo para quebra de hash MD5
def brute_force2():
# for para fazer a quebra de cada um dos possiveis 7 caracteres
    for p7 in characters2:
        for p6 in characters:
            for p5 in characters:
                for p4 in characters:
                    for p3 in characters:
                        for p2 in characters:
                            for p1 in characters:
                            
                                # um if para quando a hash for de 5 caracteres
                                palavra5 = "%s%s%s%s%s"%(p5,p4,p3,p2,p1)
                                hash5 = (hashlib.md5(palavra5.encode())).hexdigest()

                                if hash5 in hashes1:
                                    out = open("./saida.txt","a")
                                    resultado = hash5 + "," + palavra5 + "\n"
                                    print(resultado)
                                    out.write(resultado)
                                    out.close()
                                
                                # um if para quando a hash for de 6 caracteres
                                palavra6 = "%s%s%s%s%s%s"%(p6,p5,p4,p3,p2,p1)
                                hash6 = (hashlib.md5(palavra6.encode())).hexdigest()

                                if hash6 in hashes1:
                                    out = open("./saida.txt","a")
                                    resultado = hash6 + "," + palavra6 + "\n"
                                    print(resultado)
                                    out.write(resultado)
                                    out.close()
                                
                                # um if para quando a hash for de 6 caracteres
                                palavra7 = "%s%s%s%s%s%s%s"%(p7,p6,p5,p4,p3,p2,p1)
                                hash7 = (hashlib.md5(palavra7.encode())).hexdigest()

                                if hash7 in hashes1:
                                    out = open("./saida.txt","a") 
                                    resultado = hash7 + "," + palavra7 + "\n"
                                    print(resultado)
                                    out.write(resultado)
                                    out.close()

# usando threads para melhorar a velocidade das quebras dessas hashes MD5
t = Thread(target=brute_force1, args=())
t.start()

s = Thread(target=brute_force2, args=())
s.start()
 ~~~
 
 # Hashes a Serem Quebradas
 
Hashes                          | String      |
:------------------------------:|:-----------:|
59275c0a57c1912eba3b237d2bc57d6c|1r(/e        | 
0978496b93e1071dc7c40a81e95c3925|             |
742e6fde3ea050e413ee491f0290354a|             |
07208f17a430a235ceefc8a856b57f56|             |
42c76757ae2b89a1ae9e7d3f2f918aac|             |
c1491ad8c03e2ada58d3e7d773041723|             |
50aea0edbb9c8b91a810ad7f2e90b568|             |
dd1df27fef89eb9b0364c3803fcf4ceb|2p#?g        | 
8b365f0fd77f4a8b29b22fa9b3f46d2c|             |
5c281ef353b00703e224fae631403440| 4l!|k       |
6eba2afd08b788a46def38c420580240|             |
eb9b0daccbff5f6be60d241263720955|9b-<u        |
82c8a24e125df09ce18906eda3e25062|0y*\c        |
751c39690fb8071c7292776d7b6a638f|             |
6c066f396461ba8831088bcf8c2e8c19|             |
b5197cebb685d19c1ffab146e9125783|             |
f649f3c248152f0e43638ac6cbc06594|             |
47cb7cc4c1d3c8a0eb2afb5f9ce64377|3n()i        |
95650081a595315bd36c2801f2c120af|             |
c5dd4880f4aa1d623f28651afec2ed4a|             |
c46901272edfbe7730df9ff09518edb2|5j$+m        |
8215e46a79498744224eb239cf100dc2|             |
c5781aa76d4e4315f09f1c2c5afa04a8|             |
8d9a372b47cf443cac9f097420538f05|             |
61650746431e6c31ae845520b2a69ea2|             |
d69e23084c0be871c5f95ed2ead45ffc|             |
f8e15734344f8bdd5026fa1852b89487|             |
04b78196fdc6ffe443618571deb25846|6h@}o        |
a7af447f4133a73d3418fda6e650fcd3|7f#=q        |
29733d63917ebcda6c88ba69da1b25a2|8d%>s        |

 

 
