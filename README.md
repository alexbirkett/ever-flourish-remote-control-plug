GNU Radio for EverFlourish remote control plug
==============================================


## Objective
This is my first foray into GNURadio. The objective of this project is to decode the messages sent by a EverFlourish plug socket remote control using GNU Radio Companion, idealy without using any custom blocks.


## The remote control and plug

<a href="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/remote-and-plug1.jpg"><img src="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/remote-and-plug1.jpg"/></a>

<a href="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/remote-and-plug2.jpg"><img src="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/remote-and-plug2.jpg"/></a>


Purchased from Clas Ohlson in norway. Available [here](http://www.clasohlson.com/no/Fjernstyrt-bryter-3-pack/36-3570)


## Remote control recording


The file remote_control_recording contains a recording of all buttons on the remote control being pressed. The buttons were pressed in the following order:

* Button 1 On
* Button 1 Off
* Button 2 On
* Button 2 Off
* Button 3 On
* Button 3 Off


This sqeuence was repeated on all 'channels' (A though D). 

The recording was made using the EverFlourish.grc flowgraph on GNU Radio 3.7.1 using a USRP N210. The same flowgraph can playback the recording.

### Opening in Baudline

The recording can be opened in the [Baudline](http://www.baudline.com/) signal analyser. The following settings should be used

* File type - raw
* Sample rate - custom 250000
* Decode format - 32 bit float le endian
* Channels - 2 (enable quadrature)

<a href="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/baudline_import.png"><img src="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/baudline_import.png"/></a>

#### Closeup of waveform showing long and short pulses
<a href="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/waveform1.png"><img src="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/waveform1.png"/></a>
#### Waveform showing complete message
<a href="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/waveform2.png"><img src="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/waveform2.png"/></a>


## RF Protocol

My hypothesis is that the device uses [OOK modulation](http://en.wikipedia.org/wiki/On-off_keying). 

When a button on the remote control is held down a message is repeatedly broadcast. The message is 33.6 ms long and is followed by 10.4 ms of silence. The message is built up of 25 pulses of carrier. There appear to be two types of pulses:

* Long - 975 µs of carrier followed by 332 of silence
* Short - 344 µs of carrier followed by 1002 µs of silence




### Pulses

S = short pulse
L = long pulse

<table>
<tr>
	<th>
		Channel
	</th>
	<th>
		Socket
	</th>
	<th>
		On / Off
	</th>
	<th>
		Pulses
	</th>
</tr>

<tr>
<td rowspan="6">A</td>
</td>
<td rowspan="2">1</td>
</td>
<td>On</td>
<td>SSSLSLSLSSSLSLSLSLSLSLLLS</td>
</td>
</tr>


<tr>
<td>Off</td>
<td>SSSLSLSLSSSLSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">2</td>
</td>
<td>On</td>
<td>SSSLSLSLSLSSSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SSSLSLSLSLSSSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">3</td>
</td>
<td>On</td>
<td>SSSLSLSLSLSLSSSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SSSLSLSLSLSLSSSLSLSLSLSSS</td>
</td>
</tr>

<tr>
<td rowspan="6">B</td>
</td>
<td rowspan="2">1</td>
</td>
<td>On</td>
<td>SLSSSLSLSSSLSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSSSLSLSSSLSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">2</td>
</td>
<td>On</td>
<td>SLSSSLSLSLSSSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSSSLSLSLSSSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">3</td>
</td>
<td>On</td>
<td>SLSSSLSLSLSLSSSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSSSLSLSLSLSSSLSLSLSLSSS</td>
</td>
</tr>

<tr>
<td rowspan="6">C</td>
</td>
<td rowspan="2">1</td>
</td>
<td>On</td>
<td>SLSLSSSLSSSLSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSLSSSLSSSLSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">2</td>
</td>
<td>On</td>
<td>SLSLSSSLSLSSSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSLSSSLSLSSSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">3</td>
</td>
<td>On</td>
<td>SLSLSSSLSLSLSSSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSLSSSLSLSLSSSLSLSLSLSSS</td>
</td>
</tr>

<tr>
<td rowspan="6">D</td>
</td>
<td rowspan="2">1</td>
</td>
<td>On</td>
<td>SLSLSLSSSSSLSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSLSLSSSSSLSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">2</td>
</td>
<td>On</td>
<td>SLSLSLSSSLSSSLSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSLSLSSSLSSSLSLSLSLSLSSS</td>
</td>
</tr>

<tr>
</td>
<td rowspan="2">3</td>
</td>
<td>On</td>
<td>SLSLSLSSSLSLSSSLSLSLSLLLS</td>
</td>
</tr>

<tr>
<td>Off</td>
<td>SLSLSLSSSLSLSSSLSLSLSLSSS</td>
</td>
</tr>

</table>

## Decoding

### Converting sinusoids to square pulses
This can be achived using the Complex to Mag^2 block

#### Message waveform after being passed through Complex to Mag^2 block 
<a href="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/square_pulse.png"><img src="https://raw.github.com/alexbirkett/ever-flourish-remote-control-plug/master/images/square_pulse.png"/></a>




## Links

[Key Fob Lab: Demodulating Over the Air OOK](http://www.ni.com/white-paper/13192/en/)

[Discussion on Reddit](http://www.reddit.com/r/GNURadio/comments/1mgfkc/ook_remote_control/)


