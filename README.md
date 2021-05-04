# GUIDES

### Installation

1. Download package

	```curl https://bitcoin.org/bin/bitcoin-core-0.21.0/bitcoin-0.21.0-x86_64-linux-gnu.tar.gz --out bitcoin-0.21.0-x86_64-linux-gnu.tar.gz```

2. Download the list of cryptographic checksums
		
	```curl https://bitcoincore.org/bin/bitcoin-core-0.21.0/SHA256SUMS.asc --out SHA256SUMS.asc```

3. Verify that the checksum of the release file is listed in the checksums file using the following command

	```sha256sum --ignore-missing --check SHA256SUMS.asc```

4. Obtain a copy of the release signing key

	```gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 01EA5486DE18A882D4C2684590C8019E36C2E964```

5. Verify that the checksum file is PGP signed by the release signing key

	```gpg --verify SHA256SUMS.asc```

6. Check the output from the above command for the following text:
	
	1. A line that starts with: ```gpg: Good signature```
	2. A complete line saying:
```Primary key fingerprint: 01EA 5486 DE18 A882 D4C2  6845 90C8 019E 36C2 E964```

7. Install package
	```
	tar xzvf bitcoin-0.21.0-x86_64-linux-gnu.tar.gz
	sudo install -m 0755 -o root -g root -t /usr/local/bin bitcoin-0.21.0/bin/*
	```

8. Run bitcoin coin core daemon (with 10GB to allot for raw block & undo data)
	```
	bitcoind -prune=10000 -daemon
	```
