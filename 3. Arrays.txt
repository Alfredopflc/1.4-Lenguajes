.data
a: .skip 400
b: .skip 8
.text
.global main
main:
	ldr r1, =a @ r1 <- &a
	mov r2, #0 @ r2 <- 0
Loop:
	cmp r2, #100 @ Have we reached 100 yet?
	beq end @ If so, leave the loop
	add r3, r1, r2, LSL #2 @ r3 <- r1 + (r2*4)
	str r2, [r3] @ *r3 <- r2
	add r2, r2, #1 @ r2 <- r2 + 1
	b Loop @ Goto beginning of the Loop
end:
	bx lr
