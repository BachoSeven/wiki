# Wifi issues and solutions
_sauce: [linux-wifi](http://kmkeen.com/linux-wifi/)_

## Attenuation ~= weak signal

- directional antennas; better *transmitter* or *receiver*
- (lol) slow speed to improve SNR

## Noise (Città)

- directional antennas help here as well

## Contention ~= other humans

### Issues
- cannot connect
- cannot get an IP adress
- frequent timeouts on webpages
- invalid packets

### Solutions
- Increase *speed* for everybody (reduces SNR)
- *Fragment* your packets (by default they are in one piece): on Linux, `iwconfig INTERFACE frag 256` to chop them up. ~_hurts throughput_
- Enable *`rts`* handshaking: gets the attention of the AP: on Linux, `iwconfig INTERFACE rts 1` to force-enable it (default is only packets <2kB). ~_hurts throughput_
- Increase *retry* levels: default is usually 7 attempts; a more reasonable value is `iwconfig INTERFACE retry 30`.

# WPS
https://askubuntu.com/questions/120367/how-to-connect-to-wi-fi-ap-through-wps
