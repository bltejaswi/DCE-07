# DCE-07
Computer Networks project<br>
<b>DCE-07: </b>
<b>Validate the ns-3 implementation of H-TCP</b>
<p>HTCP is a congestion control protocol that is suitable for deployment in high-
speed and long-distance networks.The new protocol, H-TCP, is shown to fair when deployed in
homogeneous networks, to be friendly when competing with conventional TCP sources, to rapidly
respond to bandwidth as it becomes available, and to utilise link bandwidth in an efficient manner.
Further, when deployed in conventional networks, H-TCP behaves as a conventional TCP-variant.</p>
<b>Steps Followed :</b><br>
Change the following to parameters according to your tcp.<br>
-> std::string transport_prot = "";<br>
-> std::string linux_prot = "";<br>

1.Linux:
 -> source/ns-3-dce$./waf --run "dce-gfc-dumbbell --stack=linux" //after successful build<br>
 ->Go to utils folder and run gfc_dumbbell_parse_cwnd_v2.py //$python2 gfc_dumbbell_parse_cwnd_v2.py<br>
 ->A cwnd_data will be created in results/gfc-dumbell/. A folder will be  newly created like "06-11-2018-01-00-27" according to the current time.
->copy linux-gnuplotscriptCwnd from pcap folder into cwnd_data and plots graphs for cwnd //$gnuplot linux-gnuplotscriptCwnd<br>
->copy linux-gnuplotscriptQ from pcap and paste it along with pcap(outside pcap folder) and plot graph //$gnuplot linux-gnuplotscriptQ<br>

2.ns3:<br>
 ->source/ns-3-dce$./waf --run "dce-gfc-dumbbell --stack=ns3"//after successful build<br>
 -> A new folder is created like"06-11-2018-01-00-27".Copy a file ns3-gnuplotscriptCwnd from pcap to cwndTraces and plot graphs for cwnd.<br>
 -> Copy a file ns3-gnuplotscriptQ from pcap and paste it outside pcap folder(along with pcap folder) and plot graphs for queuelength.<br>

3.Merge graphs of Linux and ns-3:<br>
 ->Create a new folder in ns-3-dce.<br>
 ->Copy all plotme files of linux and ns3 of cwnd and queue length into the new folder created.<br>
 ->Copy gnuplotscriptComparison and gnuplotscriptComparison_Queue files into the new folder.<br>
 ->Run the above two gnuplots inorder to get the  merged plots for linux and ns3.<br>
4.Tried by increasing  and decreasing  the datarate and obtained the graphs.<br> 
5.Went through the ns-3 implementation by comparing with the algorithm given in the paper.<br>
6.Disabled dsack,rack,fack in linux.<br>
7.Disabled sack in linux and ns-3.
