1 Introduction
==============

While developing [IPFS, the InterPlanetary FileSystem](https://ipfs.io/), we came to learn about several challenges imposed by having to run a distributed file system on top of heterogeneous devices, with different network setups and capabilities.
[IPFS, InterPlanetary FileSystem] (https://ipfs.io/)을 개발하면서 다양한 네트워크 설정 및 기능을 사용하여 이기종 장치 위에 분산 파일 시스템을 실행해야하는 몇 가지 문제에 대해 알아 냈습니다.

During this process, we had to revisit the whole network stack and elaborate solutions to overcome the obstacles imposed by design decisions of the several layers and protocols, without breaking compatibility or recreating technologies.
이 과정에서 우리는 전체 네트워크 스택을 재검토하고 호환성이나 재 설계 기술을 깨지 않고 여러 계층과 프로토콜의 설계 결정에서 부과 된 장애물을 극복하기위한 솔루션을 정교하게해야했습니다.

In order to build this library, we focused on tackling problems independently, creating less complex solutions with powerful abstractions that, when composed, can offer an environment for a peer-to-peer application to work successfully.
이 라이브러리를 구축하기 위해 우리는 문제를 독자적으로 다루는 데 중점을 두었습니다. 강력한 추상화를 통해 덜 복잡한 솔루션을 만들었습니다. 구성하면 피어 투 피어 응용 프로그램이 성공적으로 작동 할 수있는 환경을 제공 할 수 있습니다

## 1.1 Motivation

`libp2p` is the result of our collective experience of building a distributed system, in that it puts responsibility on developers to decide how they want an app to interoperate with others in the network, and favors configuration and extensibility instead of making assumptions about the network setup.

In essence, a peer using `libp2p` should be able to communicate with another peer using a variety of different transports, including connection relay, and talk over different protocols, negotiated on demand.

## 1.2 Goals

Our goals for the `libp2p` specification and its implementations are:

  - Enable the use of various:
    - transports: TCP, UDP, SCTP, UDT, uTP, QUIC, SSH, etc.
    - authenticated transports: TLS, DTLS, CurveCP, SSH
  - Make efficient use of sockets (connection reuse)
  - Enable communications between peers to be multiplexed over one socket (avoiding handshake overhead)
  - Enable multiprotocols and respective versions to be used between peers, using a negotiation process
  - Be backwards compatible
  - Work in current systems
  - Use the full capabilities of current network technologies
  - Have NAT traversal
  - Enable connections to be relayed
  - Enable encrypted channels
  - Make efficient use of underlying transports (e.g. native stream muxing, native auth, etc.)
