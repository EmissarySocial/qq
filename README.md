# qq

[![GoDoc](https://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)](http://pkg.go.dev/github.com/EmissarySocial/qq)
[![Build Status](https://img.shields.io/github/actions/workflow/status/EmissarySocial/qq/go.yml?branch=main)](https://github.com/EmissarySocial/qq/actions/workflows/go.yml)
[![Codecov](https://img.shields.io/codecov/c/github/EmissarySocial/qq.svg?style=flat-square)](https://codecov.io/gh/EmissarySocial/qq)
[![Go Report Card](https://goreportcard.com/badge/github.com/EmissarySocial/qq?style=flat-square)](https://goreportcard.com/report/github.com/EmissarySocial/qq)
[![Version](https://img.shields.io/github/v/release/EmissarySocial/qq?include_prereleases&style=flat-square&color=brightgreen)](https://github.com/EmissarySocial/qq/releases)
![Lines of Code](https://shields.io/tokei/lines/github.com/EmissarySocial/qq)

<img alt="AI Generated Sherlock Holmes" src="https://github.com/EmissarySocial/qq/raw/main/meta/chariot-race.jpg" style="width:100%; display:block; margin-bottom:20px;">

## An Overly Simplistic Message Queue

QQ (Queue of Queues) is a message queue with as few moving parts as possible.  It is being developed initially for handling outbound HTTP requests for the [Emissary project](https://github.com/EmissarySocial/emissary) with the hope that this style of message queue may be useful for other projects in the future.

QQ supports a wide variety of workloads, with is main feature being that messages in each channel are delivered sequentially, and that failed message deliveries in any particular channel will block subsequent messages in that same channel but will not block other channels.  However, messages to different channels (typically to different external servers) may be delivered out of order.

QQ is not a high-performance, high-throughput message queue, as there are plenty of more rigorous message queues out there for this purpose.  Instead, it is made to be simple to use and install, with as few external dependencies as possible.  This initial version supports MongoDB, but QQ should be easy to port to other NoSQL databases, and I'll be happy to help anyone who's interested in undertaking this task.

## Using QQ

```go

func main() {
	queue := qqmongo.New("ConnectionString").WithWorkerCount(128)
	queue.Start()
}
```

## Pull Requests Welcome

Steranko is a work in progress, and will benefit from your experience reports, use cases, and contributions.  If you have an idea for making this library better, send in a pull request.  We're all in this together! 🔐
