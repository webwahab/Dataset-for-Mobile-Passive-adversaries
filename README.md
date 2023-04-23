# Dataset-for-Mobile-Passive-adversaries

This project describes the process of generating synthetic data of mobile passive attacks in vehicular networks.
The generation of synthetic data is based on a set of algorithms emulating normal behavior and attacker behaviors.
The use of synthetic data allows the development of more accurate ML models since synthetic data can encompass all the envisioned scenarios. 
Indeed,  it is hard to cover all the possible cases by simulations or by experiments. 
The generation of synthetic data is based on the distance between the target and the attacker. 
In practice, each vehicle periodically stores the distance between itself and neighboring vehicles. 
The figure below illustrates the parameters used to generate the synthetic data: 
- (i) the maximum communication range (CR); 
- (ii) the Safety Distance (SD); 
- (iii) the Caution Distance (CD), which is the distance that the attacker keeps avoiding visual detection by the target; 
- (iv) the Reaction Distance (RD), which is an additional margin of distance that the attacker may take while it is trying to adapt its speed with the attacker's speed to maintain the CD. 
This mainly occurs when encountering obstacles like other vehicles.

<p align="center">
  <img src="https://user-images.githubusercontent.com/6827382/233789278-8d6b4c2f-ffed-48e8-8994-938b79736d10.png"/>
</p>

Algorithm 1 shows the pseudo-codes of the algorithms used to generate synthetic data. n is the number of normal
vehicles, m is the number of taken measures. nc is the number of constant attackers, nas is the number of attack-and-stop attackers, P is a period to switch between attack and no-attack
in the attack-and-stop strategy, nr is the number of random attackers, ncl is the total number of collaborative attackers and ng is the size of a group of collaborative attackers.
- Subroutine 1 is used to generate a trace of normal vehicles. The variations of the inter-distance between vehicles are random and can range from the limit of SD to the limit of CR.
- Subroutine 2 is used to generate a trace of constant attackers. As already mentioned this attacker tries to keep a CD to avoid being noticed by the target.  It always tries to adapt its speed within the reaction zone to maintain the CD.
- Subroutine 3 is used to generate a trace of attack-and-stop attackers. This attacker periodically alternates between attack and normal. $P$ is the period used to switch between the normal and the attack modes.
- Subroutine 4 is used to generate a trace to random attackers. Unlike the attack-and-stop attacker, the attacker randomly switches the normal and the attack modes.
- Subroutine 5 is used to generate a trace of collaborative attackers.  These attackers are organized in groups. Attackers of each group synchronize between themselves, where each attacker uses a single attack strategy. For example, in the pseudo-code, collaborative attackers use a constant strategy. The pseudo-code applies the highway strategy since the urban strategy consists of single attackers geographically distributed, which can be generated using the previous subroutines. 


<p align="center">
  <img src="https://user-images.githubusercontent.com/6827382/233834242-d0b06b8b-fc2e-4033-9d79-11d92b325028.png"/>
</p>

For more information about the use of this dataset, please refer to the following publication:


@article{boualouache2022federated,\n
  title={Federated learning-based scheme for detecting passive mobile attackers in 5g vehicular edge computing},\\
  author={Boualouache, Abdelwahab and Engel, Thomas},
  journal={Annals of Telecommunications},
  pages={1--20},
  year={2022},
  publisher={Springer}
}
