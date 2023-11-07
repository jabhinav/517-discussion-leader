# Review

## Info

Reviewer Name: Abhinav Jain
Paper Title: Deconstructing Process Isolation. Mark Aiken, Manuel Fähndrich, Chris Hawblitzel, Galen Hunt, James Larus. Microsoft Research

## Summary
The paper provides a valuable perspective on the trade-offs between security, performance, and flexibility in process isolation. The introduction of SIPs and Protection Domains demonstrates a novel approach to tackling the limitations of traditional hardware-based protection mechanisms. 

### Problem and why we care
Traditional operating systems rely on hardware-based process isolation, which incurs performance overhead and limits fine-grain isolation. This restricts their ability to provide efficient and secure execution environments for applications and extensions.

### Gap in current approaches
Increased IPC cost due to
- Address Translation overhead
- Context Switching involving higher-privileged component
- Copying Data

### Hypothesis, Key Idea, or Main Claim
The key idea in Singularity is the introduction of Software Isolated Processes (SIPs) and Protection Domains as a more efficient and flexible means of achieving isolation. SIPs use software verification instead of hardware protection to decouple, reducing the performance overhead associated with later.

### Method for Proving the Claim
The paper provides a detailed description of the Singularity operating system and its design principles, along with performance benchmarks compared to traditional operating systems.

### Method for evaluating
The paper uses micro and macro benchmarks to assess the performance of SIPs and Protection Domains in Singularity.

### Contributions: what we take away
- Use of Language-based safety verification during static analysis to enforce process isolation.
- Hardware and Software based isolations can be combined in different ways based on the requirements.
- Singularity's design principles provide insights into balancing performance and security.

### Pros (3-6 bullets)
- Fine-grain isolation with SIPs improves security and fault tolerance.
- Reduced performance overhead compared to traditional hardware-based protection mechanisms.
- Flexibility in memory management and process termination simplification.

### Cons (3-6 bullets)
- Transitioning to SIPs may require significant changes to existing OS architectures.
- The effectiveness of SIPs depends on how well the type-saftey system of the language is written, if erroneous could compromise the security of the whole system.
- The additional layers of verification and untethered fine-grain isolation through many SIPs could impact the execution speed of certain applications.

### What is your analysis of the proposed?
(Summarize and justify what your evluation of the paper is.) 

The paper addresses the need for fine-grain isolation while reducing performance overhead. However, the practicality of transitioning to this model and the potential impact on existing systems will require further investigation and consideration. The benchmark results indicate the promise of this approach, but real-world adoption will likely depend on use-case-specific requirements and the willingness of developers to adopt this.

### Details Comments, Observations, Questions
- I have no idea why software based isolation is not widely adopted.
- I want to see what other advanced static checks can be used to implement OS design aspects other than process isolation.

## Research Questions
- Explore the implications of having SIPs at the kernel level (Ring 0).
- Discuss the trade-offs between shared memory and SIPs enabling processes to independently allocate and reclaim their own memory.
- In what ways you can optimize inter-process communication across domain boundaries?
- When do you think hardware induced protection outweighs the software induced?
- Singularity used Sing #, an in-house developed dialect of C#. What other type—safe languages you think you can use and why?
- I believe Singularity was a research project which never saw commercial adoption. Why is that?
- What design principles from Singularity could be incorporated into modern OSs to address the challenges of scalability and resource management? How can modern OS design benefit from Singularity's emphasis on fine-grain isolation using software isolated processes (SIPs) and hardware protection domains? What are the potential trade-offs to consider?



