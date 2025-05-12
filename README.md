# rendez-Vous server library written in Go

[![GoDoc](https://godoc.org/github.com/Link-3DS/Rendez-Vous?status.svg)](https://godoc.org/github.com/Link-3DS/Rendez-Vous)

### Install

`go get github.com/Link-3DS/Rendez-Vous`

### Usage note

This module provides a barebones PRUDP server for use with titles using the Nintendo NEX library. It does not provide any support for titles using the original Rendez-Vous library developed by Quazal. This library only provides the low level packet data, as such it is recommended to use [NEX Protocols Go](https://github.com/PretendoNetwork/nex-protocols-go) to develop servers.

### Usage

```Golang
package main

import (
	"fmt"

	nex "github.com/Link-3DS/Rendez-Vous"
)

func main() {
	server := nex.NewServer() // Handle Server
	server.SetPrudpVersion(0) // PRUDP Version
	server.SetSignatureVersion(1) // Signature Version
	server.SetKerberosKeySize(16) // Kerberos Key Size
	server.SetAccessKey("ridfebb9") // Access Key

	server.On("Data", func(packet *nex.PacketV0) {
		// Handle Data Packet
	})

	server.Listen(":60000") // Listen UDP
}
```