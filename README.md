<p align="center">
<img src="https://img.shields.io/badge/sclang%203.11.1-SuperCollider-orange?style=for-the-badge"/>
<img src="https://img.shields.io/badge/neovim-scnvim-orange?style=for-the-badge&logo=neovim"/>
<img src="https://img.shields.io/badge/lua-slowly%20learning-orange?style=for-the-badge&logo=lua"/>
<img src="https://img.shields.io/badge/rust-on%20arm-orange?style=for-the-badge&logo=rust"/>

## Everyday usage

* play{SawDPW.ar(666)!666}
* s.volume_(666)
	* bufmaps 
	```
function M.scnvim()
	local opts = { nowait = true, noremap = true, silent = true }

	-- Buffer local mappings:
	-- Mode, keys, mapping
	local bufmaps = {
		-- Start sclang
		{'n', '<F1>', ':SCNvimStart<CR>'},

		-- Recompile
		{'n', '<leader>sk', ':SCNvimRecompile<CR>'},

		-- Boot server
		{'n', '<leader>b', M.scnvim_send("Server.local.boot")},

		-- Servermeter
		{'n', '<F2>', M.scnvim_send("Server.local.meter")},

		-- Plot nodetree
		{'n', '<F3>', M.scnvim_send("Server.local.nodeTree")},

		-- Clear post window
		{'n', '<F4>', ':call scnvim#postwindow#clear()<CR>'},

		{'n', '<silent><buffer><F8>', M.scnvim_send('if(s.isRecording){s.stopRecording}{s.record("~/.local/share/SuperCollider/Recordings"+/+PathName(thisProcess.nowExecutingPath).fileNameWithoutExtension+/+Date.localtime.stamp++".wav", numChannels: s.options.recChannels)}')},

		-- Hard stop
		{'n', '<F12>', M.scnvim_send("thisProcess.hardStop")},

		-- Echo args
		{'n', ';', ':call scnvim#util#echo_args()<CR>'},

		-- Regenerate Ctags
		{'n', '<leader>rt', ':SCNvimTags<CR>'},

		-- Look up implementation for class under cursor
		{'n', '<leader>si', 'g]'}
	}

M.bufmaps(bufmaps, opts)
	end
	```
