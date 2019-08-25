#+=================================================================================+
# |Author : Hrudhay Kolli
# |Creation date : 08-Sep-2018
# |Modified On : 01-Mar-2019
# |Version : 
# |Catagory : MT and DB
# |DESCRIPTION : To append provided certificates
# |PLATFORM : Linux
#+=================================================================================+



#!/bin/ksh
echo -e "Type of Certficate you want to add"
echo -e "\n1) Punchout to iSupplier(B64)\n2) Punchout to XML gateway\n3) DB wallet Certificates\n4) MT Wallet - 12.1(Apache)\n0) Exit"
echo -en "\nEnter your choice : "
read input

########################################################################
#						Declaring Global Variables
########################################################################

backup=`echo '_bkp_\`date +%d%b%y_%T\`'`


########################################################################
#							Sub Functions
########################################################################

Create_Folder_Script()
{
	if [ ! -d "/ood_repository/scripts/$rfc" ]
	then
	        mkdir -m 777 -p /ood_repository/scripts/$rfc

	else
	        cp -rf /ood_repository/scripts/$rfc /ood_repository/scripts/"$rfc"_`(date +%d%b%y_%T)`
	        # rm -rf /ood_repository/scripts/$rfc
	        mkdir -m 777 -p /ood_repository/scripts/$rfc
	fi
}


Verifying_certificate()
{

	echo -en "\nEnter no of certificates to be added : "
	read noc

	#Local Variables
	no=1;
	noc=$noc;
	while [ $no -le $noc ]
	do 
	echo -en "\nEnter the absolute path of the new file location $no : "
	read nfl #nfl - New File Location
	echo $nfl > /ood_repository/scripts/$rfc/temp$no.txt

	if [ ! -f `cat /ood_repository/scripts/$rfc/temp$no.txt` ]
	then
	    echo "`cat /ood_repository/scripts/$rfc/temp$no.txt` not found"
	    exit

	else
		#Checking if the provided file is a valid certificate
		chmod 755 /ood_repository/scripts/$rfc/cert_display.txt>/ood_repository/scripts/$rfc/cert_display.txt
		orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt` > /ood_repository/scripts/$rfc/cert_display.txt

		if [ `grep -q 'invalid certificate' /ood_repository/scripts/$rfc/cert_display.txt && echo $?` ] || [ `grep -q 'Unable to read certificate' /ood_repository/scripts/$rfc/cert_display.txt && echo $?` ];then
			echo -e "\nInvalid Certificate"
			echo -e "\nPlease check and enter correct certificate, else update support/customer to get the correct certificate"
			if [ ! -f /ood_repository/custom_scripts/$x/MT/$rfc.sh ];then
				rm /ood_repository/custom_scripts/$x/MT/$rfc.sh
			elif [ ! -f /ood_repository/custom_scripts/$x/DB/$rfc.sh ];then
				rm /ood_repository/custom_scripts/$x/DB/$rfc.sh
			fi
			exit
		else
			echo -e "\nValid Certificate"
		fi
	fi
    no=`expr $no + 1`
    done
}



########################################################################
#                            Main Functions
########################################################################

Punchout_to_iSupplier()
{

	plan1()

	{
	echo -e "\nFINDINGS:"
	echo -e "\n---------"
	echo -e "\nVersion      :$version"
	echo -e "\nProfile Name :POR: Certificate File Name"
	echo -e "\nValue        : $path"
	    #Local Variables
	no=1;
	noc=$noc;
	while [ $no -le $noc ]
	do
		echo -e "\n\nCertificate Details :"
		echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
		orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
	    no=`expr $no + 1`
	done
	echo -e "\nFINAL ACTION PLAN:"
	echo -e "====================="
	echo -e "\n1. Perform Pre Health Checks"
	echo -e "\n2. Login to MT node as 'ap' user"
	echo -e "\n3. Take backup of below file :"
	echo -e "\n     -- $path"
	#Local Variables
	no=1;
	noc=$noc;

	while [ $no -le $noc ]
	do 
		echo -e "\n4-$no. Append the contents of '`cat /ood_repository/scripts/$rfc/temp$no.txt`' to the begining of $path"
		echo -e "\ncat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'"
		echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"
		no=`expr $no + 1`
	done
	echo -e "\n5. Bounce MT Services"
	echo -e "\n6. Perform Post Health checks "
	echo -e "\nEstimated Timings"
	echo -e "Window :  Outage"
	echo -e "Time   :  3Hrs"

	}



	plan2()
	{
	echo -e "\nFINDINGS:"
	echo -e "\n---------"
	echo -e "\nVersion      :$version"
	echo -e "\nProfile Name :POR: Certificate File Name"
	echo -e "\nValue        : $path"
	#Local Variables
	no=1;
	noc=$noc;
	while [ $no -le $noc ]
	do
		echo -e "\n\nCertificate Details :"
		echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
		orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
	    no=`expr $no + 1`
	done
	echo -e "\nFINAL ACTION PLAN:"
	echo -e "\n====================="
	echo -e "\n1. Perform Pre Health Checks"
	echo -e "\n2. Login to MT node as 'ap' user"
	echo -e "\n3. Take backup of below file :"
	echo -e "\n     -- $path"
	#Local Variables
	no=1;
	noc=$noc;

	while [ $no -le $noc ]
	do 
		echo -e "\n4-$no. Append the contents of '`cat /ood_repository/scripts/$rfc/temp$no.txt`' to the end of $path"
		echo -e "\n     cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path"
		no=`expr $no + 1`
	done
	echo -e "\n5. Bounce MT Services"
	echo -e "\n6. Perform Post Health checks "
	echo -e "\nEstimated Timings"
	echo -e "Window :  Outage"
	echo -e "Time   :  3Hrs"
	}

	plan3()

	{
	echo -e "\nFINAL ACTION PLAN:"
	echo -e "====================="
	echo -e "\n1. Perform Pre Health Checks"
	echo -e "\n2. Login to MT node as 'ap' user"
	echo -e "\n3. Take backup of below file :"
	echo -e "\n     -- $path"
	echo -e "\n     -- $path2"
	#Local Variables
	no=1;
	noc=$noc;

	while [ $no -le $noc ]
	do 
		echo -e "\n4-$no. Append the contents of '`cat /ood_repository/scripts/$rfc/temp$no.txt`' to the begining of $path and $path2"
		echo -e "\ncat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'"
		echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"
		echo -e "\ncat $path2 >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'"
		echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path2"
		no=`expr $no + 1`
	done
	echo -e "\n5. Bounce MT Services"
	echo -e "\n6. Perform Post Health checks "
	echo -e "\nEstimated Timings"
	echo -e "Window :  Outage"
	echo -e "Time   :  3Hrs"

	}



	plan4()
	{
	echo -e "\nFINAL ACTION PLAN:"
	echo -e "\n====================="
	echo -e "\n1. Perform Pre Health Checks"
	echo -e "\n2. Login to MT node as 'ap' user"
	echo -e "\n3. Take backup of below file :"
	echo -e "\n     -- $path"
	echo -e "\n     -- $path2"
	#Local Variables
	no=1;
	noc=$noc;

	while [ $no -le $noc ]
	do 
		echo -e "\n4-$no. Append the contents of '`cat /ood_repository/scripts/$rfc/temp$no.txt`' to the end of $path and $path2"
		echo -e "\n     cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path"
		echo -e "\n     cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path2"
		no=`expr $no + 1`
	done
	echo -e "\n5. Bounce MT Services"
	echo -e "\n6. Perform Post Health checks "
	echo -e "\nEstimated Timings"
	echo -e "Window :  Outage"
	echo -e "Time   :  3Hrs"
	}

	execution_plan()
	{

	echo -e "\n############################################################################"
	echo -e "\nEXECUTION PLAN"
	echo -e "##############"
	echo -e "\n1. Perform Pre Health Checks"
	echo -e "\n2. Execute the Script /ood_repository/custom_scripts/$x/MT/$rfc.sh"
	echo -e "\n3. Bounce MT Services"
	echo -e "\n4. Perform Post Health checks"
	}


	Atom_script()
	{

	    x=`id -nu | cut -c 3- | tr '[a-z]' '[A-Z]';`;
	    if [[ ! -e /ood_repository/custom_scripts/$x/DB ]]; then
	            mkdir -m 777 -p /ood_repository/custom_scripts/$x/DB
	    fi
	    if [[ ! -e /ood_repository/custom_scripts/$x/MT ]]; then
	            mkdir -m 777 -p /ood_repository/custom_scripts/$x/MT
	    fi

	    echo -en "\nEnter RFC Number: "
	    read rfc

	    cd /ood_repository/custom_scripts/$x/MT
	    if [ ! -f "$rfc.sh" ]
	    then
	            chmod 755 $rfc.sh>$rfc.sh
	    else
	            cp $rfc.sh $rfc.sh_`date +%d%b%y_%T`
	            rm /ood_repository/custom_scripts/$x/MT/$rfc.sh
	            chmod 755 $rfc.sh>$rfc.sh
	    fi

	}


Atom_script
Create_Folder_Script
Verifying_certificate

echo -n "Enter apps password :"
read -s APPS_PASSWORD
version=$(sqlplus -s apps/$APPS_PASSWORD <<EOC
SET NEWPAGE 0
SET SPACE 0
SET LINESIZE 80
SET PAGESIZE 0
SET ECHO OFF
SET FEEDBACK OFF
SET HEADING OFF
set termout off
SET VERIFY OFF
select release_name from apps.fnd_product_groups;
exit
EOC
)

path=$(sqlplus -s apps/$APPS_PASSWORD <<EOC
SET NEWPAGE 0
SET SPACE 0
SET LINESIZE 80
SET PAGESIZE 0
SET ECHO OFF
SET FEEDBACK OFF
SET HEADING OFF
set termout off
SET VERIFY OFF
select b.PROFILE_OPTION_VALUE from fnd_profile_options_vl a,FND_PROFILE_OPTION_VALUES b where a.USER_PROFILE_OPTION_NAME in (select USER_PROFILE_OPTION_NAME from fnd_profile_options_vl where PROFILE_OPTION_NAME in ('POR_CACERT_FILE_NAME')) and a.PROFILE_OPTION_ID=b.PROFILE_OPTION_ID and b.LEVEL_ID=10001;
exit
EOC
)


ver=${version:0:4}
if [ $ver == 12.1 ]
then

	if [ ! -f $path ]
	then
	    echo -e "\n\n$path not found\n\n"
	    exit

	else
	
		echo -e "\necho -e 'Taking backup of file $path'" >> $rfc.sh
		echo -e "cp $path $path$backup"  >> $rfc.sh
		echo -e "\necho -e 'Executing the Action'" >> $rfc.sh

		echo -en "\nEnter where you want to append the text : "
		echo -en " 1) Begining    2) End   :  "
		read place

		if [ $place == 1 ]; then
		#Local Variables
		no=1;
		noc=$noc;

		while [ $no -le $noc ]
		do 
			echo -e "cat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
			echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"  >> $rfc.sh
			no=`expr $no + 1`
		done
		plan1
		execution_plan

		elif [ $place == 2 ];then
		#Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do 
			echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path\n" >> $rfc.sh
			no=`expr $no + 1`
		done
		plan2
		execution_plan

		else
		echo -e "\nInvalid option"
		fi  
	fi
																			
elif [ $ver == 12.2 ];then 
	Atom_script
	fs=${path:16:3}
	len=${#path}

	if [ ! -f $path ]
	then
	    echo -e "\n\n$path not found\n\n"
	    exit

	else

	echo -en "\nEnter where you want to append the text : "
	echo -en " 1) Begining    2) End   :  "
	read place

	if [ $place == 1 ]; then

		if [ $fs == fs2 ];then
			path2=${path:0:15}/fs1${path:19:$len}
			echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
			echo -e "cp $path $path$backup"  >> $rfc.sh
			echo -e "cp $path2 $path2$backup"  >> $rfc.sh
			echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do 
				echo -e "cat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"  >> $rfc.sh
				echo -e "cat $path2 >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path2"  >> $rfc.sh
				no=`expr $no + 1`
			done
			echo -e "\nFINDINGS:"
			echo -e "\n---------"
			echo -e "\nVersion      :$version"
			echo -e "\nProfile Name :POR: Certificate File Name"
			echo -e "\nValue        : $path"
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do
				echo -e "\n\nCertificate Details :"
				echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
				orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
			    no=`expr $no + 1`
			done
			plan3
			execution_plan


		elif [ $fs == fs1 ];then
			path2=${path:0:15}/fs2${path:19:$len}
			echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
			echo -e "cp $path $path$backup"  >> $rfc.sh
			echo -e "cp $path2 $path2$backup"  >> $rfc.sh
			echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do 
				echo -e "cat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"  >> $rfc.sh
				echo -e "cat $path2 >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path2"  >> $rfc.sh
				no=`expr $no + 1`
			done
			echo -e "\nFINDINGS:"
			echo -e "\n---------"
			echo -e "\nVersion      :$version"
			echo -e "\nProfile Name :POR: Certificate File Name"
			echo -e "\nValue        : $path"
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do
				echo -e "\n\nCertificate Details :"
				echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
				orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
			    no=`expr $no + 1`
			done
			plan3
			execution_plan

		else
			c_v=`grep -i web_ssl_certchainfile $CONTEXT_FILE` #context_file_value
			path=`echo $c_v | awk -F '>' '{print $2}' | awk -F '<' '{print $1}'`
			fs=${path:16:3}
			if [ $fs == fs2 ];then
			path2=${path:0:15}/fs1${path:19:$len}
			echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
			echo -e "cp $path $path$backup"  >> $rfc.sh
			echo -e "cp $path2 $path2$backup"  >> $rfc.sh
			echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do 
				echo -e "cat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"  >> $rfc.sh
				echo -e "cat $path2 >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path2"  >> $rfc.sh
				no=`expr $no + 1`
			done
			echo -e "\nFINDINGS:"
			echo -e "\n---------"
			echo -e "\nVersion           : $version"
			echo -e "\nContext Variable  : web_ssl_certchainfile"
			echo -e "\nValue             : $path"
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do
				echo -e "\n\nCertificate Details :"
				echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
				orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
			    no=`expr $no + 1`
			done
			plan3
			execution_plan



			elif [ $fs == fs1 ];then
			path2=${path:0:15}/fs2${path:19:$len}
			echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
			echo -e "cp $path $path$backup"  >> $rfc.sh
			echo -e "cp $path2 $path2$backup"  >> $rfc.sh
			echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do 
				echo -e "cat $path >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path"  >> $rfc.sh
				echo -e "cat $path2 >> '`cat /ood_repository/scripts/$rfc/temp$no.txt`'" >> $rfc.sh
				echo -e "mv '`cat /ood_repository/scripts/$rfc/temp$no.txt`' $path2"  >> $rfc.sh
				no=`expr $no + 1`
			done
			echo -e "\nFINDINGS:"
			echo -e "\n---------"
			echo -e "\nVersion           : $version"
			echo -e "\nContext Variable  : web_ssl_certchainfile"
			echo -e "\nValue             : $path"
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do
				echo -e "\n\nCertificate Details :"
				echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
				orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
			    no=`expr $no + 1`
			done
			plan3
			execution_plan
			fi

		fi

	elif [ $place == 2 ];then

		if [ $fs == fs2 ];then
			path2=${path:0:15}/fs1${path:19:$len}
			echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
			echo -e "cp $path $path$backup"  >> $rfc.sh
			echo -e "cp $path2 $path2$backup"  >> $rfc.sh
			echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do 
				echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path\n" >> $rfc.sh
				echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path2\n" >> $rfc.sh
				no=`expr $no + 1`
			done
			echo -e "\nFINDINGS:"
			echo -e "\n---------"
			echo -e "\nVersion      :$version"
			echo -e "\nProfile Name :POR: Certificate File Name"
			echo -e "\nValue        : $path"	
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do
				echo -e "\n\nCertificate Details :"
				echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
				orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
			    no=`expr $no + 1`
			done		
			plan4
			execution_plan

		elif [ $fs == fs1 ];then
			path2=${path:0:15}/fs2${path:19:$len}
			echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
			echo -e "cp $path $path$backup"  >> $rfc.sh
			echo -e "cp $path2 $path2$backup"  >> $rfc.sh
			echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do 
				echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path\n" >> $rfc.sh
				echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path2\n" >> $rfc.sh
				no=`expr $no + 1`
			done
			echo -e "\nFINDINGS:"
			echo -e "\n---------"
			echo -e "\nVersion      :$version"
			echo -e "\nProfile Name :POR: Certificate File Name"
			echo -e "\nValue        : $path"
			#Local Variables
			no=1;
			noc=$noc;
			while [ $no -le $noc ]
			do
				echo -e "\n\nCertificate Details :"
				echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
				orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
			    no=`expr $no + 1`
			done			
			plan4
			execution_plan

		else
			c_v=`grep -i web_ssl_certchainfile $CONTEXT_FILE` #context_file_value
			path=`echo $c_v | awk -F '>' '{print $2}' | awk -F '<' '{print $1}'`
			if [ ! -f $path ]
			then
			    echo -e "\n\n$path not found\n\n"
			    exit

			else
				fs=${path:16:3}
				if [ $fs == fs2 ];then
				path2=${path:0:15}/fs1${path:19:$len}
				echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
				echo -e "cp $path $path$backup"  >> $rfc.sh
				echo -e "cp $path2 $path2$backup"  >> $rfc.sh
				echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
				#Local Variables
				no=1;
				noc=$noc;
				while [ $no -le $noc ]
				do 
					echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path\n" >> $rfc.sh
					echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path2\n" >> $rfc.sh
					no=`expr $no + 1`
				done
				echo -e "\nFINDINGS:"
				echo -e "\n---------"
				echo -e "\nVersion           : $version"
				echo -e "\nContext Variable  : web_ssl_certchainfile"
				echo -e "\nValue             : $path"
				#Local Variables
				no=1;
				noc=$noc;
				while [ $no -le $noc ]
				do
					echo -e "\n\nCertificate Details :"
					echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
					orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
				    no=`expr $no + 1`
				done
				plan4
				execution_plan


				elif [ $fs == fs1 ];then
				path2=${path:0:15}/fs2${path:19:$len}
				echo -e "\necho -e 'Taking backup of file $path and $path2'" >> $rfc.sh
				echo -e "cp $path $path$backup"  >> $rfc.sh
				echo -e "cp $path2 $path2$backup"  >> $rfc.sh
				echo -e "\necho -e 'Executing the Action'" >> $rfc.sh
				#Local Variables
				no=1;
				noc=$noc;
				while [ $no -le $noc ]
				do 
					echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path\n" >> $rfc.sh
					echo -e "cat '`cat /ood_repository/scripts/$rfc/temp$no.txt`' >> $path2\n" >> $rfc.sh
					no=`expr $no + 1`
				done
				echo -e "\nFINDINGS:"
				echo -e "\n---------"
				echo -e "\nVersion           : $version"
				echo -e "\nContext Variable  : web_ssl_certchainfile"
				echo -e "\nValue             : $path"	
				#Local Variables
				no=1;
				noc=$noc;
				while [ $no -le $noc ]
				do
					echo -e "\n\nCertificate Details :"
					echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
					orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
				    no=`expr $no + 1`
				done		
				plan4
				execution_plan
				fi
			fi
	

		fi

	fi
fi

else 
	echo -e "\nInvalid Version of host or incorrect APPS password"
fi


}


DB_wallet_Certificates()
{


	Findings_new()
	{
	    echo -e "\n\n\nFINDINGS:"
	    echo -e "\n################"
	    echo -e "\nWallet is not present in the instance, hence action plan includes creation of wallet"
	    #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
	}


	Findings_WE() #Findings_Wallet_Existing
	{
	    echo -e "\n\n\nFINDINGS:"
	    echo -e "\n################"
	    echo -e "\nWallet existing :-"
	    echo -e "\n----------------------"
	    echo -e "\nWallet location:- $ORACLE_HOME/appsutil/wallet "
	    cd $ORACLE_HOME/appsutil/wallet
	    echo -e '\nls -lhtr ewallet.p12* cwallet.sso*'
	    echo -e "\n`ls -lhtr ewallet.p12* cwallet.sso*`"
	    echo -e "\nDisplaying wallet:-"
	    echo -e "\n`orapki wallet display -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd`"
	    #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
	}

	Findings_RW() #Findings_Recreating_Wallet
	{
	    echo -e "\n\n\nFINDINGS:"
	    echo -e "\n################"
	    echo -e "\nWallet existing :-"
	    echo -e "\n----------------------"
	    echo -e "\nWallet location:- $ORACLE_HOME/appsutil/wallet "
	    cd $ORACLE_HOME/appsutil/wallet
	    echo -e '\nls -lhtr ewallet.p12* cwallet.sso*'
	    echo -e "\n`ls -lhtr ewallet.p12* cwallet.sso*`"
	    echo -e "\nWallet is present in the instance, but unable to validate the password, hence action plan includes re-creation of wallet"
	    #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
	}

	Findings_WE_CE() #Findings_Wallet_Existing_Certificate_Existing
	{
	    echo -e "\n\n\nFINDINGS:"
	    echo -e "\n################"
	    echo -e "\nWallet existing :-"
	    echo -e "\n----------------------"
	    echo -e "\nWallet location:- $ORACLE_HOME/appsutil/wallet "
	    cd $ORACLE_HOME/appsutil/wallet
	    echo -e '\nls -lhtr ewallet.p12* cwallet.sso*'
	    echo -e "\n`ls -lhtr ewallet.p12* cwallet.sso*`"
	    echo -e "\nDisplaying wallet:-"
	    echo -e "\n`orapki wallet display -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd`"
	    echo -e "\n---------------------------------------------------------------\n"
	    echo -e "\n   --->  Provided Certificate(/s) exists is the wallet\n"
	    echo -e "\n---------------------------------------------------------------\n"
	    #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
	}

	Action_plan_new()
	{
	    echo -e "\nFINAL ACTION PLAN:"
	    echo -e "\n====================="
	    echo -e "\n1. Login to DB node as 'or' user"
	    echo -e "\n2. Create New Wallet Directory :-"
	    echo -e '\n     -- mkdir -m 750 -p $ORACLE_HOME/appsutil/wallet'
	    echo -e "\n3. Generate new password and append it to a file :-"
	    echo -e '\n     -- randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}'
	    echo -e '\n     -- randpw>/ood_repository/scripts/$rfc/pswd.txt'
	    echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'
	    echo -e "\n4. Create New Wallet :-"
	    echo -e '\n     -- orapki wallet create -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd -auto_login'
	    echo -e "\n5. Add certificate to the wallet:-"
	    #Local Variables
		no=1;
		noc=$noc;

	    while [ $no -le $noc ]
		do
		    echo -e '\n     -- orapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
		    no=`expr $no + 1`
		done
	    echo -e "\n6. Verify the new certificate in the wallet:-"
	    echo -e '\n     -- orapki wallet display -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd'
	    echo -e "\n7. Delete the wallet password file :"
	    echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
	    echo -e "\nEstimated Timings"
	    echo -e "Window :  Service"
	    echo -e "Time   :  3Hrs"
	}

	Action_plan_RW() #Action plan including re-creation of wallet
	{
	    echo -e "\nFINAL ACTION PLAN:"
	    echo -e "\n====================="
	    echo -e "\n1. Login to DB node as 'or' user"
	    echo -e "\n2. Take backup of existing wallet directory :-"
	    echo -e '\n     -- cp '$ORACLE_HOME/appsutil/wallet $ORACLE_HOME/appsutil/wallet$backup
	    echo -e "\n3. Delete the existing wallet directory :-"
	    echo -e "\n     -- rm -rf "$ORACLE_HOME/appsutil/wallet 
	    echo -e "\n4. Create New Wallet Directory :-"
	    echo -e "\n     -- mkdir -m 750 -p $ORACLE_HOME/appsutil/wallet"
	    echo -e "\n5. Generate new password and append it to a file :-"
	    echo -e '\n     -- randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}'
	    echo -e '\n     -- randpw>/ood_repository/scripts/$rfc/pswd.txt'
	    echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'
	    echo -e "\n6. Create New Wallet :-"
	    echo -e '\n     -- orapki wallet create -wallet '$ORACLE_HOME/appsutil/wallet' -pwd $pswd -auto_login'
	    echo -e "\n7. Add certificate to the wallet:-"
	   	#Local Variables
		no=1;
		noc=$noc;

	   	while [ $no -le $noc ]
		do
	    	echo -e '\n     -- orapki wallet add -wallet '$ORACLE_HOME/appsutil/wallet' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
		    no=`expr $no + 1`
		done	    
	    echo -e "\n8. Verify the new certificate in the wallet:-"
	    echo -e '\n     -- orapki wallet display -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd'
	    echo -e "\n9. Delete the wallet password file :"
	    echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
	    echo -e "\nEstimated Timings"
	    echo -e "Window :  Service"
	    echo -e "Time   :  3Hrs"
	}



	Action_plan_WE() #Action_plan_Wallet_Existing
	{
	    echo -e "\nFINAL ACTION PLAN:"
	    echo -e "\n====================="
	    echo -e "\n1. Login to DB node as 'or' user"
	    echo -e "\n2. Take backup of existing wallet directory :"
	    echo -e '\n     -- cp '$ORACLE_HOME/appsutil/wallet $ORACLE_HOME/appsutil/wallet$backup
	    echo -e "\n3. Please use the following for the wallet password(the provided password is appended into the respective text file):-"
	    echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'  
	    echo -e "\n4. Add certificate to the wallet:-"
	   	#Local Variables
		no=1;
		noc=$noc;

	   	while [ $no -le $noc ]
		do
	    	echo -e '\n     -- orapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
		    no=`expr $no + 1`
		done
	    echo -e "\n5. Verify the new certificate in the wallet:-"
	    echo -e '\n     -- orapki wallet display -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd'
	    echo -e "\n6.Delete the wallet password file :"
	    echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
	    echo -e "\nEstimated Timings"
	    echo -e "Window :  Service"
	    echo -e "Time   :  3Hrs"  
	}


	Action_plan_WE_CE() #Action_plan_Wallet_Existing_Certificate_Existing
	{
	    echo -e "\nFINAL ACTION PLAN:"
	    echo -e "\n====================="
	    echo -e "\n1. Login to DB node as 'or' user"
	    echo -e "\n2. Take backup of existing wallet directory :"
	    echo -e '\n     -- cp '$ORACLE_HOME/appsutil/wallet $ORACLE_HOME/appsutil/wallet$backup
	    echo -e "\n3. Please use the following for the wallet password(the provided password is appended into the respective text file):-"
	    echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'  
	    echo -e "\n4. Remove the existing certificate:-"
	    #echo -e '\n     -- orapki wallet remove -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -dn '"$cert_value"
	    cat /ood_repository/scripts/$rfc/action_plan.txt
	    echo -e "\n5. Add certificate to the wallet:-"
	   	#Local Variables
		no=1;
		noc=$noc;
	   	while [ $no -le $noc ]
		do
	    	echo -e '\n     -- orapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
		    no=`expr $no + 1`
		done	    	
	    echo -e "\n6. Verify the new certificate in the wallet:-"
	    echo -e '\n     -- orapki wallet display -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd'
	    echo -e "\n7. Delete the wallet password file :"
	    echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
	    echo -e "\nEstimated Timings"
	    echo -e "Window :  Service"
	    echo -e "Time   :  3Hrs"  
	}

	Execution_plan()
	{
	    echo -e "\n############################################################################"
	    echo -e "\nEXECUTION PLAN"
	    echo -e "##############"
	    echo -e "\n1. Execute the Script /ood_repository/custom_scripts/$x/DB/$rfc.sh"

	}



	Atom_script()
	{

	    x=`id -nu | cut -c 3- | tr '[a-z]' '[A-Z]';`;
	    if [[ ! -e /ood_repository/custom_scripts/$x/DB ]]; then
	            mkdir -m 777 -p /ood_repository/custom_scripts/$x/DB
	    fi
	    if [[ ! -e /ood_repository/custom_scripts/$x/MT ]]; then
	            mkdir -m 777 -p /ood_repository/custom_scripts/$x/MT
	    fi

	    echo -en "\nEnter RFC Number: "
	    read rfc

	    cd /ood_repository/custom_scripts/$x/DB
	    if [ ! -f "$rfc.sh" ]
	    then
	            chmod 755 $rfc.sh>$rfc.sh
	    else
	            cp $rfc.sh $rfc.sh_`date +%d%b%y_%T`
	            rm /ood_repository/custom_scripts/$x/DB/$rfc.sh
	            chmod 755 $rfc.sh>$rfc.sh
	    fi

	}


	Verifying_wallet()
	{		
		cd /ood_repository/custom_scripts/$x/DB
        echo -e "\n#Verification" >> $rfc.sh
        echo -e '\ncd $ORACLE_HOME/appsutil/wallet' >> $rfc.sh
        echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
        echo -e '\norapki wallet display -wallet . -pwd $pswd' >> $rfc.sh
        echo -e "\nls -lhtr ewallet.p12 cwallet.sso" >> $rfc.sh
        echo -e "\nrm /ood_repository/scripts/$rfc/pswd.txt" >> $rfc.sh
	}

	Remove_Certificate()
	{

        cd /ood_repository/custom_scripts/$x/DB
        echo -e "\n#Removing the existing certificate" >> $rfc.sh
		cert_value=`cat /ood_repository/scripts/$rfc/cert_summary.txt | awk -F ':' '{print $2}'|awk 'sub(/^ */, "")'`
    	echo -e '\n orapki wallet remove -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -dn ''"'"$cert_value"'"' >> $rfc.sh               
    	echo -e '\n     -- orapki wallet remove -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -dn '"$cert_value" >> /ood_repository/scripts/$rfc/action_plan.txt
	}

	Adding_certificate_new_wallet()
	{

    	Verifying_certificate
        #Checking if the provided certificate already exists in the wallet
    	#Local Variables
		no=1;
		noc=$noc;
        while [ $no -le $noc ]
		do
		echo $no
	        chmod 755 /ood_repository/scripts/$rfc/cert_summary.txt>/ood_repository/scripts/$rfc/cert_summary.txt
	        orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt` -summary | grep -i Subject >/ood_repository/scripts/$rfc/cert_summary.txt
	        cert_sum=`cat /ood_repository/scripts/$rfc/cert_summary.txt`
	        cd $ORACLE_HOME/appsutil/wallet
	        orapki wallet display -wallet . -pwd $pswd | grep -i Subject >/ood_repository/scripts/$rfc/wallet_summary.txt

	        if [ "z$cert_sum" != "z" ]; then

	            if [ `grep -i "$cert_sum" /ood_repository/scripts/$rfc/wallet_summary.txt |wc -l` != 0 ]; then
	                #echo -e "\n\nUpdate customer that the certificate exists in the wallet"
	                #Remove the existing certificate
	                Remove_Certificate
	            	#Adding certificate
	                echo -e "\n#Adding certificate" >> $rfc.sh
	                echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
	                echo -e '\norapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
	                #exit
   				else
                #Adding certificate
                cd /ood_repository/custom_scripts/$x/DB
                echo -e "\n#Adding certificate" >> $rfc.sh
                echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
                echo -e '\norapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
            	fi
	    	fi 
        no=`expr $no + 1`
		done
	
	}


	Adding_certificate()
	{

    	Verifying_certificate
    	#Local Variables
		no=1;
		noc=$noc;
        while [ $no -le $noc ]
		do
		#Checking if the provided certificate already exists in the wallet
		chmod 755 /ood_repository/scripts/$rfc/cert_summary.txt>/ood_repository/scripts/$rfc/cert_summary.txt
		orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt` -summary | grep -i Subject >/ood_repository/scripts/$rfc/cert_summary.txt
		cert_sum=`cat /ood_repository/scripts/$rfc/cert_summary.txt`
		cd $ORACLE_HOME/appsutil/wallet
		orapki wallet display -wallet . -pwd $pswd | grep -i Subject >/ood_repository/scripts/$rfc/wallet_summary.txt

		if [ "z$cert_sum" != "z" ]; then
	        if [ `grep -i "$cert_sum" /ood_repository/scripts/$rfc/wallet_summary.txt |wc -l` != 0 ]; then
		        #echo -e "\n\nUpdate customer that the certificate exists in the wallet"
		        #Remove the existing certificate
		        Remove_Certificate
		        #Adding certificate
		        echo -e "\n#Adding certificate" >> $rfc.sh
	            echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
	            echo -e '\norapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
                if [ $no -eq $noc ]
                then
	                Findings_WE_CE
	                Action_plan_WE_CE
	                break;
	            fi
		        #exit

	        else
	            #Adding certificate
	            cd /ood_repository/custom_scripts/$x/DB
	            echo -e "\n#Adding certificate" >> $rfc.sh
	            echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
	            echo -e '\norapki wallet add -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
	            if [ $no -eq $noc ] 
	            then
		            Findings_WE
		            Action_plan_WE
		            break;
		        fi
        	fi
       	fi
        no=`expr $no + 1`
        done
        	
   
	}


    Recreate_Wallet()
    {
            
        cd /ood_repository/custom_scripts/$x/DB
        echo -e "\n#Taking backup of and deleting existing wallet" >> $rfc.sh
        echo -e '\ncp '$ORACLE_HOME/appsutil/wallet $ORACLE_HOME/appsutil/wallet$backup >> $rfc.sh
        echo -e "\nrm -rf "$ORACLE_HOME/appsutil/wallet >> $rfc.sh
        #Generating new password
        randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}
        randpw>/ood_repository/scripts/$rfc/pswd.txt
        pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`
        echo -e "\n#Creating new wallet" >> $rfc.sh
        echo -e '\nmkdir -m 750 -p '$ORACLE_HOME/appsutil/wallet >> $rfc.sh
        echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
        echo -e '\norapki wallet create -wallet '$ORACLE_HOME/appsutil/wallet' -pwd $pswd -auto_login' >> $rfc.sh
        Adding_certificate_new_wallet
        Verifying_wallet
        Findings_RW
        Action_plan_RW
        Execution_plan
    }



	New_wallet()
	{
		#Creating new wallet
        Atom_script
        Create_Folder_Script
        cd /ood_repository/custom_scripts/$x/DB
        chmod 755 /ood_repository/scripts/$rfc/findings.txt>/ood_repository/scripts/$rfc/findings.txt
		chmod 755 /ood_repository/scripts/$rfc/action_plan.txt>/ood_repository/scripts/$rfc/action_plan.txt
        #Generating new password
        randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}
        randpw>/ood_repository/scripts/$rfc/pswd.txt
        pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`
        echo -e "\n#Creating new wallet" >> $rfc.sh
        echo -e '\nmkdir -m 750 -p $ORACLE_HOME/appsutil/wallet' >> $rfc.sh
        echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
        echo -e '\norapki wallet create -wallet $ORACLE_HOME/appsutil/wallet -pwd $pswd -auto_login' >> $rfc.sh
        cd /ood_repository/custom_scripts/$x/DB
		Adding_certificate_new_wallet
        Verifying_wallet
        Findings_new
        Action_plan_new
        Execution_plan
	}

	Existing_wallet()
	{
	#Verifying the already present wallet
	        #cp -rf $ORACLE_HOME/appsutil/wallet $ORACLE_HOME/appsutil/wallet_`(date +%d%b%y_%T)`
        if [ ! -f "$ORACLE_HOME/appsutil/wallet/ewallet.p12"  ]
        then
                echo "ewallet.p12 file is not present in the directory"
        else
                Atom_script
                Create_Folder_Script
                chmod 755 /ood_repository/scripts/$rfc/findings.txt>/ood_repository/scripts/$rfc/findings.txt
				chmod 755 /ood_repository/scripts/$rfc/action_plan.txt>/ood_repository/scripts/$rfc/action_plan.txt
                cp $ORACLE_HOME/appsutil/wallet/ewallet.p12 /ood_repository/scripts/$rfc
                cd /ood_repository/scripts/$rfc
                i=0
                while [ $i -lt 3 ]
                do
                    echo -en "Enter wallet password : "
                    read -s wallet_pswd
                    echo $wallet_pswd>/ood_repository/scripts/$rfc/pswd.txt
                    pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`
                    chmod 755 wallet_display.txt>wallet_display.txt
                    orapki wallet display -wallet . -pwd $pswd > wallet_display.txt

                    if [ `grep -q 'incorrect password' wallet_display.txt && echo $?` ] || [ `grep -q 'Unable to load wallet at' wallet_display.txt && echo $?` ] || [ `grep -q 'Unable to open the wallet' wallet_display.txt && echo $?` ];then
                        echo -e "\nIncorrect password"
                        echo -e "\nPlease check and enter correct password"
                    elif [ `grep -q 'Trusted Certificates' wallet_display.txt && echo $?` ];then
                        break;
                    fi
                    i=`expr $i + 1`
                done

                if [ $i -eq 3 ];then
                    echo -en "\nDo you want to re-create the wallet ? (Yes/No) : "
                    read choice
                    if [ "$choice" = "Yes" -o "$choice" = "y" -o "$choice" = "yes" -o "$choice" = "Y" ]
                    then
                        Recreate_Wallet

                    elif [ "$choice" = "No" -o "$choice" = "n" -o "$choice" = "no" -o "$choice" = "N" ]
                    then 
                        echo -e "Please update customer and get confirmation if we can recreate the wallet"
                        rm /ood_repository/custom_scripts/$x/DB/$rfc.sh
                    else
                        echo "Invalid choice"
                        rm /ood_repository/custom_scripts/$x/DB/$rfc.sh
                    fi
                else
                    if [ `grep -q 'Trusted Certificates' wallet_display.txt && echo $?` ];then
                        cd /ood_repository/custom_scripts/$x/DB
                        echo -e "\n#Taking backup of existing wallet" >> $rfc.sh
                        echo -e '\ncp '$ORACLE_HOME/appsutil/wallet $ORACLE_HOME/appsutil/wallet$backup >> $rfc.sh
                        Adding_certificate
                        Verifying_wallet
                        Execution_plan
                    fi
                fi
        fi

	}


echo -n "Enter apps password :"
read -s APPS_PASSWORD
count=$(sqlplus -s apps/$APPS_PASSWORD <<EOC
SET NEWPAGE 0
SET SPACE 0
SET LINESIZE 80
SET PAGESIZE 0
SET ECHO OFF
SET FEEDBACK OFF
SET HEADING OFF
set termout off
SET VERIFY OFF
select count(*) from gv\$instance;
exit
EOC
)

if [ $count -gt 1 ];then
	echo -e "\n\n##################################\n"
	echo -e "\nRAC Node, please plan manually\n"
	echo -e "\n##################################\n\n"
	exit
else 
	cd $ORACLE_HOME/appsutil
	if [ ! -d "wallet"  ]
	then
	        New_wallet
	else
	        Existing_wallet
	fi

fi

}


DB_wallet_Certificates



Punchout_to_XML_gateway()
{
    echo -e "\nPunchout_to_XML_gateway\n"

}



MT_Wallet_12_1()
{
    Findings_new()
    {
        echo -e "\n\n\nFINDINGS:"
        echo -e "\n################"
        echo -e "\nApache is not present in the instance, hence action plan includes creation of wallet"
        #Sourcing the env file
        . $INST_TOP/ora/10.1.3/$env_file
       	#Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
    }


    Findings_WE() #Findings_Wallet_Existing
    {
        echo -e "\n\n\nFINDINGS:"
        echo -e "\n################"
        echo -e "\nApache existing :-"
        echo -e "\n----------------------"
        echo -e "\nApache location:- $path/Apache "
        #Sourcing the env file
        . $INST_TOP/ora/10.1.3/$env_file
        cd $path/Apache
        echo -e '\nls -lhtr ewallet.p12* cwallet.sso*'
        echo -e "\n`ls -lhtr ewallet.p12* cwallet.sso*`"
        echo -e "\nDisplaying wallet:-"
        echo -e "\n`orapki wallet display -wallet . -pwd $pswd`"
        #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
    }

    Findings_RW() #Findings_Recreating_Wallet
    {
        echo -e "\n\n\nFINDINGS:"
        echo -e "\n################"
        echo -e "\nApache existing :-"
        echo -e "\n----------------------"
        echo -e "\nApache location:- $path/Apache "
        #Sourcing the env file
        . $INST_TOP/ora/10.1.3/$env_file
        cd $path/Apache
        echo -e '\nls -lhtr ewallet.p12* cwallet.sso*'
        echo -e "\n`ls -lhtr ewallet.p12* cwallet.sso*`"
        echo -e "\nApache is present in the instance, but unable to validate the password, hence action plan includes re-creation of wallet"
        #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
    }

    Findings_WE_CE() #Findings_Wallet_Existing_Certificate_Existing
    {
        echo -e "\n\n\nFINDINGS:"
        echo -e "\n################"
        echo -e "\nApache existing :-"
        echo -e "\n----------------------"
        echo -e "\nApache location:- $path/Apache "
        #Sourcing the env file
        . $INST_TOP/ora/10.1.3/$env_file
        cd $path/Apache
        echo -e '\nls -lhtr ewallet.p12* cwallet.sso*'
        echo -e "\n`ls -lhtr ewallet.p12* cwallet.sso*`"
        echo -e "\nDisplaying wallet:-"
        echo -e "\n`orapki wallet display -wallet . -pwd $pswd`"
	    echo -e "\n---------------------------------------------------------------\n"
	    echo -e "\n   --->  Provided Certificate(/s) exists is the wallet\n"
	    echo -e "\n---------------------------------------------------------------\n"
	    #Local Variables
		no=1;
		noc=$noc;
		while [ $no -le $noc ]
		do
			echo -e "\n\nCertificate Details :"
			echo -e "\norapki cert display -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' "
			orapki cert display -cert `cat /ood_repository/scripts/$rfc/temp$no.txt`
		    no=`expr $no + 1`
		done
    }

    Action_plan_new()
    {
        echo -e "\nFINAL ACTION PLAN:"
        echo -e "\n====================="
        echo -e "\n1. Perform Pre Health Checks"
        echo -e "\n2. Login to MT node as 'ap' user"
        echo -e "\n3. Create New Wallet Directory :-"
        echo -e "\n     -- mkdir -m 750 -p $path/Apache"
        echo -e "\n4. Generate new password and append it to a file :-"
        echo -e '\n     -- randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}'
        echo -e '\n     -- randpw>/ood_repository/scripts/$rfc/pswd.txt'
        echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'
        echo -e '\n5. Source the environment file '
        echo -e '\n     -- . $INST_TOP/ora/10.1.3/'$env_file
        echo -e "\n6. Create New Wallet :-"
        echo -e '\n     -- orapki wallet create -wallet '$path/Apache' -pwd $pswd -auto_login'
        echo -e "\n7. Add certificate to the wallet:-"
        #Local Variables
		no=1;
		noc=$noc;

        while [ $no -le $noc ]
		do 
        	echo -e '\n     -- orapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
        no=`expr $no + 1`
		done
        echo -e "\n8. Verify the new certificate in the wallet:-"
        echo -e '\n     -- orapki wallet display -wallet . -pwd $pswd'
        echo -e "\n9. Delete the wallet password file :"
        echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
        echo -e "\n10. Bounce MT Services"
        echo -e "\n11. Perform Post Health checks "
        echo -e "\nEstimated Timings"
        echo -e "Window :  Outage"
        echo -e "Time   :  3Hrs"
    }



    Action_plan_RW() #Action plan including re-creation of wallet
    {
        echo -e "\nFINAL ACTION PLAN:"
        echo -e "\n====================="
        echo -e "\n1. Perform Pre Health Checks"
        echo -e "\n2. Login to MT node as 'ap' user"
        echo -e "\n3. Take backup of existing wallet directory :-"
        echo -e '\n     -- cp '$path/Apache $path/'Apache'$backup
        echo -e "\n4. Delete the existing wallet directory :-"
        echo -e "\n     -- rm -rf "$path/Apache 
        echo -e "\n5. Create New Wallet Directory :-"
        echo -e "\n     -- mkdir -m 750 -p $path/Apache"
        echo -e "\n6. Generate new password and append it to a file :-"
        echo -e '\n     -- randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}'
        echo -e '\n     -- randpw>/ood_repository/scripts/$rfc/pswd.txt'
        echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'
        echo -e '\n7. Source the environment file '
        echo -e '\n     -- . $INST_TOP/ora/10.1.3/'$env_file
        echo -e "\n8. Create New Wallet :-"
        echo -e '\n     -- orapki wallet create -wallet '$path/Apache' -pwd $pswd -auto_login'
        echo -e "\n9. Add certificate to the wallet:-"
        #Local Variables
		no=1;
		noc=$noc;

        while [ $no -le $noc ]
		do 
        	echo -e '\n     -- orapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
        no=`expr $no + 1`
		done
        echo -e "\n10. Verify the new certificate in the wallet:-"
        echo -e '\n     -- orapki wallet display -wallet . -pwd $pswd'
        echo -e "\n12. Delete the wallet password file :"
        echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
        echo -e "\n12. Bounce MT Services"
        echo -e "\n13. Perform Post Health checks "
        echo -e "\nEstimated Timings"
        echo -e "Window :  Outage"
        echo -e "Time   :  3Hrs"
    }



    Action_plan_WE() #Action_plan_Wallet_Existing
    {
        echo -e "\nFINAL ACTION PLAN:"
        echo -e "\n====================="
        echo -e "\n1. Perform Pre Health Checks"
        echo -e "\n2. Login to MT node as 'ap' user"
        echo -e "\n3. Take backup of existing wallet directory :-"
        echo -e '\n     -- cp '$path/Apache $path/'Apache'$backup
        echo -e "\n4. Please use the following for the wallet password(the provided password is appended into the respective text file):-"
        echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'  
        echo -e '\n5. Source the environment file '
        echo -e '\n     -- . $INST_TOP/ora/10.1.3/'$env_file
        echo -e "\n6. Add certificate to the wallet:-"
        #Local Variables
		no=1;
		noc=$noc;

        while [ $no -le $noc ]
		do 
        	echo -e '\n     -- orapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
        no=`expr $no + 1`
		done
        echo -e "\n7. Verify the new certificate in the wallet:-"
        echo -e '\n     -- orapki wallet display -wallet . -pwd $pswd'
        echo -e "\n8. Delete the wallet password file :"
        echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
        echo -e "\n9. Bounce MT Services"
        echo -e "\n10. Perform Post Health checks "
        echo -e "\nEstimated Timings"
        echo -e "Window :  Outage"
        echo -e "Time   :  3Hrs"  
    }


    Action_plan_WE_CE() #Action_plan_Wallet_Existing_Certificate_Existing
    {
        echo -e "\nFINAL ACTION PLAN:"
        echo -e "\n====================="
        echo -e "\n1. Perform Pre Health Checks"
        echo -e "\n2. Login to MT node as 'ap' user"
        echo -e "\n3. Take backup of existing wallet directory :-"
        echo -e '\n     -- cp '$path/Apache $path/'Apache'$backup
        echo -e "\n4. Please use the following for the wallet password(the provided password is appended into the respective text file):-"
        echo -e '\n     -- pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`'  
        echo -e '\n5. Source the environment file '
        echo -e '\n     -- . $INST_TOP/ora/10.1.3/'$env_file
        echo -e "\n6. Remove the existing certificate:-"
        #echo -e '\n     -- orapki wallet remove -wallet '$path/Apache' -trusted_cert -dn '"$cert_value"
        cat /ood_repository/scripts/$rfc/action_plan.txt
        echo -e "\n7. Add certificate to the wallet:-"
        #Local Variables
		no=1;
		noc=$noc;

        while [ $no -le $noc ]
		do 
        	echo -e '\n     -- orapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd'
        no=`expr $no + 1`
		done        
		echo -e "\n8. Verify the new certificate in the wallet:-"
        echo -e '\n     -- orapki wallet display -wallet . -pwd $pswd'
        echo -e "\n9. Delete the wallet password file :"
        echo -e "\n     -- rm /ood_repository/scripts/$rfc/pswd.txt"
        echo -e "\n10. Bounce MT Services"
        echo -e "\n11. Perform Post Health checks "
        echo -e "\nEstimated Timings"
        echo -e "Window :  Outage"
        echo -e "Time   :  3Hrs"  
    }


    Execution_plan()
    {
        echo -e "\n############################################################################"
        echo -e "\nEXECUTION PLAN"
        echo -e "##############"
        echo -e "\n1. Perform Pre Health Checks"
        echo -e "\n2. Execute the Script /ood_repository/custom_scripts/$x/MT/$rfc.sh"
        echo -e "\n3. Perform Post Health checks"
    }

	Atom_script()
	{

	    x=`id -nu | cut -c 3- | tr '[a-z]' '[A-Z]';`;
	    if [[ ! -e /ood_repository/custom_scripts/$x/DB ]]; then
	            mkdir -m 777 -p /ood_repository/custom_scripts/$x/DB
	    fi
	    if [[ ! -e /ood_repository/custom_scripts/$x/MT ]]; then
	            mkdir -m 777 -p /ood_repository/custom_scripts/$x/MT
	    fi

	    echo -en "\nEnter RFC Number: "
	    read rfc

	    cd /ood_repository/custom_scripts/$x/MT
	    if [ ! -f "$rfc.sh" ]
	    then
	            chmod 755 $rfc.sh>$rfc.sh
	    else
	            cp $rfc.sh $rfc.sh_`date +%d%b%y_%T`
	            rm /ood_repository/custom_scripts/$x/MT/$rfc.sh
	            chmod 755 $rfc.sh>$rfc.sh
	    fi

	}

    Verifying_wallet()
    {
		cd /ood_repository/custom_scripts/$x/MT
        echo -e "\n#Verification" >> $rfc.sh
        echo -e '\ncd '$path/Apache >> $rfc.sh
        echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
        echo -e '\norapki wallet display -wallet . -pwd $pswd' >> $rfc.sh
        echo -e "\nls -lhtr ewallet.p12 cwallet.sso" >> $rfc.sh
        echo -e "\nrm /ood_repository/scripts/$rfc/pswd.txt" >> $rfc.sh
    }
        
	Remove_Certificate()
	{

        cd /ood_repository/custom_scripts/$x/MT
        echo -e "\n#Removing the existing certificate" >> $rfc.sh
		cert_value=`cat /ood_repository/scripts/$rfc/cert_summary.txt | awk -F ':' '{print $2}'|awk 'sub(/^ */, "")'`
    	echo -e '\n orapki wallet remove -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -dn ''"'"$cert_value"'"' >> $rfc.sh               
    	echo -e '\n     -- orapki wallet remove -wallet $ORACLE_HOME/appsutil/wallet -trusted_cert -dn '"$cert_value" >> /ood_repository/scripts/$rfc/action_plan.txt
	}


    Adding_certificate_new_wallet()
	{
        Verifying_certificate
        #Checking if the provided certificate already exists in the wallet
        #Local Variables
		no=1;
		noc=$noc;
        while [ $no -le $noc ]
		do
			#Sourcing the env file
	        . $INST_TOP/ora/10.1.3/$env_file

	        chmod 755 /ood_repository/scripts/$rfc/cert_summary.txt>/ood_repository/scripts/$rfc/cert_summary.txt
	        orapki cert display -cert $nfl -summary | grep -i Subject > /ood_repository/scripts/$rfc/cert_summary.txt
	        cert_sum=`cat /ood_repository/scripts/$rfc/cert_summary.txt`
	        cd $path/Apache
	        orapki wallet display -wallet . -pwd $pswd | grep -i Subject >/ood_repository/scripts/$rfc/wallet_summary.txt

	        if [ "z$cert_sum" != "z" ]; then

	            if [ `grep -i "$cert_sum" /ood_repository/scripts/$rfc/wallet_summary.txt |wc -l` != 0 ]; then
	            cd /ood_repository/custom_scripts/$x/MT

	            #Remove the existing certificate
	            Remove_Certificate

	            #Adding certificate
	            echo -e "\n#Adding certificate" >> $rfc.sh
	            echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
				echo -e '\norapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh


	        	else
	        	cd /ood_repository/custom_scripts/$x/MT
                #Adding certificate
                echo -e "\n#Adding certificate" >> $rfc.sh
                echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
				echo -e '\norapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
	        	fi
	    	fi 
        no=`expr $no + 1`
		done
    }


    Adding_certificate()
	{
        Verifying_certificate
    	#Local Variables
		no=1;
		noc=$noc;
        while [ $no -le $noc ]
		do
		#Sourcing the env file
	    . $INST_TOP/ora/10.1.3/$env_file

        #Checking if the provided certificate already exists in the wallet
        chmod 755 /ood_repository/scripts/$rfc/cert_summary.txt>/ood_repository/scripts/$rfc/cert_summary.txt
        orapki cert display -cert $nfl -summary | grep -i Subject >/ood_repository/scripts/$rfc/cert_summary.txt
        cert_sum=`cat /ood_repository/scripts/$rfc/cert_summary.txt`
        cd $path/Apache
        orapki wallet display -wallet . -pwd $pswd | grep -i Subject >/ood_repository/scripts/$rfc/wallet_summary.txt

        if [ "z$cert_sum" != "z" ]; then

            if [ `grep -i "$cert_sum" /ood_repository/scripts/$rfc/wallet_summary.txt |wc -l` != 0 ]; then
            
            cd /ood_repository/custom_scripts/$x/MT

            #Remove the existing certificate
            Remove_Certificate

            #Adding certificate
            echo -e "\n#Adding certificate" >> $rfc.sh
            echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
			echo -e '\norapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
            if [ $no -eq $noc ]
            then
                Findings_WE_CE
                Action_plan_WE_CE
                break;
            fi
            #exit

            else
            	cd /ood_repository/custom_scripts/$x/MT
                #Adding certificate
                echo -e "\n#Adding certificate" >> $rfc.sh
                echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
				echo -e '\norapki wallet add -wallet '$path/Apache' -trusted_cert -cert '`cat /ood_repository/scripts/$rfc/temp$no.txt`' -pwd $pswd' >> $rfc.sh
	            if [ $no -eq $noc ] 
	            then
	                Findings_WE
	                Action_plan_WE
	            break;
	        	fi
            fi
        fi  
        no=`expr $no + 1`
        done
        
    }


    Recreate_Apache()
    {
            
        Create_Folder_Script
        cd /ood_repository/custom_scripts/$x/MT
        echo -e "\n#Sourcing the env file " >> $rfc.sh
        echo -e '\n. $INST_TOP/ora/10.1.3/'$env_file >> $rfc.sh
        echo -e "\n#Taking backup of and deleting existing wallet" >> $rfc.sh
        echo -e '\ncp '$path/Apache $path'/Apache'$backup >> $rfc.sh
        echo -e "\nrm -rf "$path/Apache >> $rfc.sh
        #Generating new password
        randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}
        randpw>/ood_repository/scripts/$rfc/pswd.txt
        pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`
        echo -e "\n#Creating new wallet" >> $rfc.sh
        echo -e '\nmkdir -m 750 -p '$path/Apache >> $rfc.sh
        echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
        echo -e '\norapki wallet create -wallet '$path/Apache' -pwd $pswd -auto_login' >> $rfc.sh
        Adding_certificate_new_wallet
        Verifying_wallet
        Findings_RW
        Action_plan_RW
        Execution_plan
    }

	New_wallet()
	{
		#Creating new wallet
        Atom_script
        Create_Folder_Script

		#sourcing the env file
		cd $INST_TOP/ora/10.1.3
		env_file=`ls $x*env`
		. $INST_TOP/ora/10.1.3/$env_file
		cd /ood_repository/custom_scripts/$x/MT
        chmod 755 /ood_repository/scripts/$rfc/findings.txt>/ood_repository/scripts/$rfc/findings.txt
		chmod 755 /ood_repository/scripts/$rfc/action_plan.txt>/ood_repository/scripts/$rfc/action_plan.txt
        #Generating new password
        randpw(){ < /dev/urandom tr -dc A-Za-z0-9 | head -c${1:-8};echo;}
        randpw>/ood_repository/scripts/$rfc/pswd.txt
        pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`
        echo -e "\n#Sourcing the env file " >> $rfc.sh
        echo -e '\n. $INST_TOP/ora/10.1.3/'$env_file >> $rfc.sh
        echo -e "\n#Creating new wallet" >> $rfc.sh
        echo -e '\nmkdir -m 750 -p $path/Apache' >> $rfc.sh
        echo -e '\npswd=`cat /ood_repository/scripts/'$rfc'/pswd.txt`' >> $rfc.sh
        echo -e '\norapki wallet create -wallet $path/Apache -pwd $pswd -auto_login' >> $rfc.sh
        cd /ood_repository/custom_scripts/$x/MT
        Adding_certificate_new_wallet
        Verifying_wallet
        Findings_new
        Action_plan_new
        Execution_plan
	}

	Existing_wallet()
	{



		#Verifying the already present wallet
        #cp -rf $path/Apache $path/Apache_`(date +%d%b%y_%T)`
        if [ ! -f "$path/Apache/ewallet.p12"  ]
        then
                echo "ewallet.p12 file is not present in the directory"
        else
                Atom_script
                Create_Folder_Script

				#sourcing the env file
				cd $INST_TOP/ora/10.1.3
				env_file=`ls $x*env`
				. $INST_TOP/ora/10.1.3/$env_file

		        chmod 755 /ood_repository/scripts/$rfc/findings.txt>/ood_repository/scripts/$rfc/findings.txt
				chmod 755 /ood_repository/scripts/$rfc/action_plan.txt>/ood_repository/scripts/$rfc/action_plan.txt
                cp $path/Apache/ewallet.p12 /ood_repository/scripts/$rfc
                cd /ood_repository/scripts/$rfc
                i=0
                while [ $i -lt 3 ]
                do
                    echo -en "Enter wallet password : "
                    read -s wallet_pswd
                    echo $wallet_pswd>/ood_repository/scripts/$rfc/pswd.txt
                    pswd=`cat /ood_repository/scripts/$rfc/pswd.txt`
                    chmod 755 wallet_display.txt>wallet_display.txt
                    orapki wallet display -wallet . -pwd $pswd > wallet_display.txt

                    if [ `grep -q 'incorrect password' wallet_display.txt && echo $?` ] || [ `grep -q 'Unable to load wallet at' wallet_display.txt && echo $?` ];then
                        echo -e "\nIncorrect password"
                        echo -e "\nPlease check and enter correct password"
                    elif [ `grep -q 'Trusted Certificates' wallet_display.txt && echo $?` ];then
                        break;
                    fi
                    i=`expr $i + 1`
                done

                if [ $i -eq 3 ];then
                    echo -en "\nDo you want to re-create the wallet ? (Yes/No) : "
                    read choice
                    if [ "$choice" = "Yes" -o "$choice" = "y" -o "$choice" = "yes" -o "$choice" = "Y" ]
                    then
                        Recreate_Apache

                    elif [ "$choice" = "No" -o "$choice" = "n" -o "$choice" = "no" -o "$choice" = "N" ]
                    then 
                        echo -e "Please update customer and get confirmation if we can recreate the wallet"
                        rm /ood_repository/custom_scripts/$x/MT/$rfc.sh
                    else
                        echo "Invalid choice"
                        rm /ood_repository/custom_scripts/$x/MT/$rfc.sh
                    fi
                else
                    if [ `grep -q 'Trusted Certificates' wallet_display.txt && echo $?` ];then
                        cd /ood_repository/custom_scripts/$x/MT
                        echo -e "\n#Sourcing the env file " >> $rfc.sh
	            		echo -e '\n. $INST_TOP/ora/10.1.3/'$env_file >> $rfc.sh
                        echo -e "\n#Taking backup existing wallet" >> $rfc.sh
                        echo -e '\ncp '$path/Apache $path'/Apache'$backup >> $rfc.sh
                        Adding_certificate
                        Verifying_wallet
                        Execution_plan
                    fi
                fi
        fi

	}

c_v=`grep -i s_web_ssl_directory $CONTEXT_FILE`
path=`echo $c_v | awk -F '>' '{print $2}' | awk -F '<' '{print $1}'`
cd $path
if [ ! -d "Apache"  ]
then
        New_wallet
else
        Existing_wallet
fi

}

case ${input} in
    1)  ap_us;Punchout_to_iSupplier;;
    2)  Punchout_to_XML_gateway;;
    3)  or_us;DB_wallet_Certificates;;
    4)  ap_us;MT_Wallet_12_1;;
    0)  exit;;
    *)  echo -e "\nInvalid option";;
esac
