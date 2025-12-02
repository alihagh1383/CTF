**Forensics**
```

The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log. Download the encoded data here: Logs Data. Be prepared—the file is large, and examining it thoroughly is crucial .

```
[Logs Data](https://challenge-files.picoctf.net/c_amiable_citadel/eb3bef3ff1c8111665bbec934c3208346c59d291f2417a91dd70305589c16ceb/logs.txt)

---

# Solve

#### S 1
> base64 -d logs.txt > decode.txt|

#### S 2
> cat decode.txt  | less

```

<89>PNG
^Z
^@^@^@^MIHDR^@^@^C<80>^@^@^D<80>^H^B^@^@^@!<F1><B4><8E>^@^A^@^@IDATx<9C><EC><FD><D7><D3>,ɕ'<88><FD><CE>q<8F><88>^T<9F><BA><A2><EA><96>^F<AA>^Z<BA><D0><D8>Fczzg<DA>fi\<D2>h<B6>�O4<92>^?^X<9F><F8>F
<F2>m^_<97>fC[<DB>^^<EE>^L<A7><D9>3<8D>^F^F<A2>ESC<A8>^BJ<E1><D6>՟<CA>̈p<F7>s<F8>p""=է<AE><A8>jq<EC><DA>w3##<\^^-<E8><F5>^O<FE>/^@HA^C(<A9>*<89>^BP<B6>^K "0T5j^T^Q"u<CE>9"UE"f&<F2>"^R"TՏ<A6><E3><F1>
<B8><9C>L<8A><A2>89;y<F6><EC>YU2^QQ<AC><94><DA><C3><C3>CR<99><CD>fm]<D7>u<ED><DD><E8><F6><ED><DB>
<D3><E9><FE>|>o^Q<EB><BA><F6><A3>7<BF><FB><DD><EF>^V<E3><D7>^V<8B>Ÿ<D4>^PB^Q^_<FE><F5>_<FF><F5><EC><E1>'

```

#### S 3
> cp decode.txt decode.png

#### S 4
**In Image is a text like HEX** 

#### S 5
> echo -n `<HEX Text>` | xxd -r -p