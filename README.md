GNU Radio for EverFlourish remote control plug
==============================================

[Device being tested is available here](http://www.clasohlson.com/no/Fjernstyrt-bryter-3-pack/36-3570)


## Remote control recording


The file remote_control_recording contains a recording of all buttons on the remote control being pressed. The buttons were pressed in the following order:

* Button 1 On
* Button 1 Off
* Button 2 On
* Button 2 Off
* Button 3 On
* Button 3 Off


This sqeuence was repeated on 'channels' (A though D). 

The recording was made using the EverFlourish.grc flowgraph on GNU Radio 3.7.1 using a USRP N210. The same flowgraph can playback the recording.

## Decoding the signal

My hypothesis is that the device uses [OOK modulation](http://en.wikipedia.org/wiki/On-off_keying). 

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

## Links

[Key Fob Lab: Demodulating Over the Air OOK](http://www.ni.com/white-paper/13192/en/)


