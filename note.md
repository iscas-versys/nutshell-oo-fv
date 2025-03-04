关于nutshell的几个问题需要考虑一下

1、 pipeline follower访存部分的考虑需要解决几个问题

（1） 我现在已经拿到了相关的memReq的信号，但是我还是很难说是哪个CPU发出的
如果可以拿到的话就可以根据moq中的内容传递下去
（2） 传到后面之后就可以根据说memReq的内容和参考模型中的mem连接在一起.

通过dmem的resp部分确实可以很快地确定说哪一个指令进行的操作，但是我需要的是哪一个
指令发出的访存信号.
对于store指令来说， 流水线先写到store queue, 然后当具备条件的时候
就可以对dcache进行req, 因此我们看起来说store的过程比较复杂，但是实际上
对于参考模型来说， 只需要说取出写入store queue的指令对应的pipeline follower即可