system
	core
		default nix
		- security.nix (include yubikey)
		- boot.nix
	hardware
		bluetooth.nix
		opengl.nix
	network 
		default.nix (include ssh and network manager options)
	programs
		--
	nix
		nixpkgs
home 
	home manager