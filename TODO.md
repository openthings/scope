# Error

## 2016-12-25, run make
* Arch: ARM64
* Hardware: 96Boards
* CPU: Snapdragon 410C
* OS: Debian 
* Source: https://github.com/openthings/scope, branch ARM64

```
docker run --rm -ti \
	-v /media/linaro/zdata/src/github.com/openthings/scope:/go/src/github.com/weaveworks/scope \
	-v /media/linaro/zdata/src/github.com/openthings/scope/.pkg:/go/pkg \
	--net=host \
	-e GOARCH -e GOOS -e CIRCLECI -e CIRCLE_BUILD_NUM -e CIRCLE_NODE_TOTAL \
	-e CIRCLE_NODE_INDEX -e COVERDIR -e SLOW -e TESTDIRS \
	weaveworks/scope-backend-build SCOPE_VERSION=05869ab GO_BUILD_INSTALL_DEPS=-i prog/scope
make: Entering directory '/go/src/github.com/weaveworks/scope'
rm -f render/detailed/detailed.codecgen.go; unset GOOS GOARCH; env GOGC=off go build -i -ldflags "-extldflags \"-static\" -X main.version=05869ab -s -w" -tags 'netgo unsafe' ./render/detailed # workaround for https://github.com/ugorji/go/issues/145
# github.com/weaveworks/scope/probe/endpoint
probe/endpoint/reporter.go:37: undefined: DNSSnooper
Makefile:90: recipe for target 'render/detailed/detailed.codecgen.go' failed
make: *** [render/detailed/detailed.codecgen.go] Error 2
make: Leaving directory '/go/src/github.com/weaveworks/scope'
Makefile:67: recipe for target 'prog/scope' failed
make: *** [prog/scope] Error 2
```