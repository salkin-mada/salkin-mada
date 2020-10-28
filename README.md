<p align="center">
<img src="https://img.shields.io/badge/sclang%203.11.1-SuperCollider-orange?style=for-the-badge"/>
<img src="https://img.shields.io/badge/neovim-scnvim-orange?style=for-the-badge&logo=neovim"/>
<img src="https://img.shields.io/badge/lua-slowly%20learning-orange?style=for-the-badge&logo=lua"/>
<img src="https://img.shields.io/badge/rust-on%20arm-orange?style=for-the-badge&logo=rust"/>

## Everyday usage

* `play{SawDPW.ar(666)!666}`
* `s.volume_(666)`

	```lua
function M.scnvim_record()
	local opts = { nowait = true, noremap = true, silent = true }
	local mapping = {
		{'n', '<buffer><F8>', M.scnvim_send('if(s.isRecording)
				{s.stopRecording}{s.record("~/.local/share/SuperCollider/Recordings"
						+/+PathName(thisProcess.nowExecutingPath).fileNameWithoutExtension
						+/+Date.localtime.stamp++".wav", numChannels: s.options.recChannels)
				}')
		},
	}
M.mapping(mapping, opts)
	end
	```
