# simple-vdf2

[![Travis-CI Build Status](https://travis-ci.org/l3laze/vdf-parser.svg?branch=master)](https://travis-ci.org/l3laze/vdf-parser?branch=master) [![Codecov branch](https://img.shields.io/codecov/c/github/l3laze/vdf-parser.svg)](https://codecov.io/gh/l3laze/vdf-parser/list/master/) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/031fda68bad64e7aa16fbbcf6b4718b5)](https://www.codacy.com/app/l3laze/vdf-parser)

[![Dev Dependencies](https://img.shields.io/david/dev/expressjs/express.svg)](https://github.com/l3laze/vdf-parser/tree/master) [![Peer Dependencies](https://img.shields.io/david/peer/webcomponents/generator-element.svg)](https://github.com/l3laze/vdf-parser/tree/master)

[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)

----

> A Simple library for Text-based VDF (Valve Data Format) (de)serialization.

Based on l3laze's [simple-vdf2](https://github.com/l3laze/vdf-parser) which is based on Rossen Georgiev's [simple-vdf](https://www.npmjs.com/package/simple-vdf).

## methods

### parse(string[,string])
Parse a string containing VDF and returns an object.

First string is the VDF in its entirety
Second string is a special string that's passed to postpend to duplicate keys.

### stringify(obj[,boolean,string]) / dump(obj[,boolean,string])
Serializes an object to a string of VDF.

Object is the JSON to stringify.
Boolean is whether or not ot make the VDF output pretty (Indendentations)
String is an OPTIONAL string to strip from duplicate postpended keys

## modification in mstan variant

Backwards compatible with l3laze's iteration of simple-vdf. 

By default, previous implementations of simple-vdf did NOT support any object that contained duplicate keys (for example, classloadoutpanel.res in TF2's HUD files contains multiple "animations" in the same object).

In this implementation, an optional string parameter is available in parse. This is something that will be postpended to any duplicate keys. (For example, if "animation" already exists in JSON, a second animation will become "animation-KEY-2", "animation-KEY-3"...). The same key will need to be provided in stringify/dump in order to strip that key back out. (Providing a different key from a parse will have undesirable results)

Without supplying the optional string, the old behavior will occur, in which duplicates will override each other (and the last one will be the one that results).

