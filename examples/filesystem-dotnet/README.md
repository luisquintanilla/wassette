# Filesystem Example (.NET)

This is the .NET 10 equivalent of `filesystem-rs`, with the same read/write
tool names and a restrictive storage policy. The WIT world explicitly imports
WASI filesystem preopens and types; .NET `System.IO` calls are compiled for
WASI and remain subject to the runtime's preopen/policy boundary.

```bash
dotnet build -c Release
just inject-docs examples/filesystem-dotnet/bin/Release/net10.0/wasi-wasm/native/filesystem-dotnet.wasm examples/filesystem-dotnet/wit
```

Grant only the directories needed for a test. The checked-in policy grants
`/tmp` read/write as a portable development fixture; production policies
should use a narrower path.
