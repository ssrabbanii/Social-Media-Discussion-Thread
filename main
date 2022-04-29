data={}
'''data={user:{'pw':pw, 'birth':birth, 'phone':phone, 'fd':[],
         'fn':firstname, 'ln':lastname}}'''
#the format of data of users

articles={}
'''articles={user_title:{user_title(#source),content,date}}'''
#format of data of articles

def reg(): #GetU #9
    fName=input("Please enter first name: ") #first name (should not be blank)
    while len(fName)==0:
        fName=input("Please enter first name: ")
    lName=input("Please enter last name: ") #last name (should not be blank)
    while len(lName)==0:
        lName=input("Please enter last name: ")
    user=input("Please enter user name: (no '_' should be used)") #final user name
    while user in data or '_' in user: #avoid repeating and covering the data
        user=input("Please enter user name: (no '_' should be used)")
    pw=input("Please enter passowrd: ") #password (should not be blank)
    while len(pw)==0:
        pw=input("Please enter passowrd again: ")
    birth=input("Please enter date of birth (DDMMYYYY)(optional): ")
    while len(birth)!=0 and len(birth)!=8:
        birth=input("Please enter date of birth again (DDMMYYYY)(optional): ")
    phone=input("Please enter phone number (optional): ")
    data[user]=({'pw':pw, 'birth':birth, 'phone':phone, 'fd':[] ,
                 'fn':fName ,'ln':lName })
    #set up user's data with user name as key
    print('User "'+user+'"'+"'s is saved!")
    return data

def setFd():
    print("You can enter nothing to stop the function.")
    user=input("Please enter the user name: ")
    while (user not in data) and (user!=""):
        user=input("The user does not exist.\nPlease enter the user name again: ")
    if user=="":
        return data
    user2=input("Please enter another user name: ")
    while (user2 not in data) and (user!=""):
        user2=input("The user does not exist.\nPlease enter the user name again: ")
    if user2=="":
        return data
    #check if the user names exist in data set
    data[user]['fd']+=[user2]
    data[user2]['fd']+=[user]
    #friendship is symmetric so user names will be recorded into one another's data
    return data 

def isFriend(X,Y):     #1
    if X in data[Y]['fd'] and Y in data[X]['fd']:
    #check data (with reference from setFd())
        return True
    else:
        return False

def isDirectSource(A,B): #2 A and B are in form of "user_title"
    if articles[B][0]==A:
    #The first (0th) term  in value set of "articles" is the source
        return True
    else:
        return False

def Anchor(A): #4 
    while articles[A][0]!='':
    #loop until there is no source for the article
        A=articles[A][0]
    return A

def isSource(A,B): #3
    while (B!=A) and (articles[B][0]!=''):
        B=articles[B][0]
    #loop until no source for the article or knowing A is source of B
    if B==A:
    #if A is source of B
        return True
    else:
    #else (if B does not directly or indirectly report A)
        return False

def DirectReport(A): #5
    l=[]
    for i in articles:
        if articles[i][0]==A:
        #search for the articles with first value (source) of A
            l+=[i]
    return l

def Report(A): #6
    l=DirectReport(A)
    for i in l:
        for j in articles:
            if articles[j][0]==i and j not in l:
        #similar to DirectReport() but add a loop which is similar to isSource()
                l+=[j]
    return l
    
def article():#GetA #10
    user=''
    while user not in data:
            user=input("Please enter the author of the article") #input author
    title=input("Title (article with a totally same title will be covered): ")
    while len(title)==0 or ('_' in title): #no '_' &not blank
        title=input("Title: ") #input title
    content=''
    q=input("Will you quote? (yes or no)") #ask for quote
    if q[0]=='y': #if yes
        useR=''
        while useR not in data: 
            useR=input("Please enter the author of the article that you want to quote")
            #repeat if the user does not exist
        titlE=''
        while useR+'_'+titlE not in articles:
            titlE=input("Please enter the title fo the article that you want to quote")
            #repeat if the article does not exist
        print(articles[useR+'_'+titlE][1],"\nPlease enter the range\n(index of starting character, index of ending character)(1,10 means quoting from 1st word to the 10th word")
        sRange,eRange=int(input("Starting index: ")),int(input("Ending index: "))
        quote=useR+'_'+titlE #record the source
        content='"'+articles[useR+'_'+titlE][1][(sRange-1):(eRange)]+'"'
        #start the content with the quote
    else:
        quote='' #no source if not quote
    content+=input("Content: ") #input content
    date=input("Date (DDMMYYYY): ") #input date
    while len(date)!=0 and len(date)!=8: #repeat if the date is not length of 8
        date=input("Date (DDMMYYYY): ")
    articles[user+'_'+title]=quote,content,date #return the data

def NicePrintU(X): #X=username #7
    lx=data[X].item() 
    print("User's Name: "+X)
    print("First Name: "+lx[4])
    print("Second Name: "+lx[5])
    print("Birthday: "+lx[1])
    print("Phone: "+lx[2])
    print("Friend(s): "+lx[3])
    password=input("Do you want to show the password (yes or no): ")
    if password=='yes':
        print("Password: "+lx[0])

def NicePrintA(A): #A=username_title #8
    t=A.split("_")
    print("Title: "+t[1])
    print("Reply: "+articles[A][0])
    print("   by: "+t[0])
    print("Content: "+articles[A][1])
    print("Date: "+articles[A][2])

def main():
    #set up 3 lists
    influenceU=data.key() #list of all users
    influenceN=[] #list of influences of all users
    KOL=[]        #list of users who can become KOLs
    for i in data: #check for every user name
        influenceA=0
        for j in articles:
            if i==j[0:len(i)]:   #check if user name in "user_title" is the required one
                influenceA+=len(DirectReport(j))
                #add the influence of the article into total influence of the user
        influenceN+=[influenceA] #record users' influences
    for i in range (0,int(len(inf)*p)):
        iN=[]+influenceN
        iU=[]+influenceU
        mx=max(iN) #find the max influence
        user=data.key[iU.index(mx)] #and also its corresponding user
        while user in KOL: #if the user already exists in KOL list, repeat until the user found does not exist in KOL list
            iN.remove(mx) #remove the maximum
            iU.remove(user) #and its corresponding user
            mx=max(influence) #then find the next maximum
            user=data.key[influence.index(mx)] #and the corresponding user 
        if mx<T: #if the influence smaller than threshold
            break #stop finding next max influence
        else:
            KOL+=[user] #else add into list of KOL
        if i==nKOL and iN.count(mx)>1: #if there is some users with same influence 
            while iN.count(mx)>0: #repeat until all of them are in the KOL list
                iN.remove(mx)  #remove the max found
                iU.remove(user) #and the user
                user=data.key[influence.index(mx)] #find the user with same influence
                KOL+=[user] #add into KOL list
    print("KOLs are "+KOL) #let the user know who are the KOLs
    print("Enter user name of the KOL whose information you want to know")
    wantedU=input("OR just enter nothing to continue explore friendship between KOLs: ")
    while wantedU !='' : #if not entering nothing
        if wantedU not in data: #if the user does not exist in data
            print("The name is not KOL") 
            wantedU=input("Please enter again: ") #let function user enter user name again 
        else: #else (user name exists)
            NicePrintU(wantedU) 
            print("Enter user name of the KOL whose information you want to know")
            wantedU=input("OR just enter nothing to continue explore friendship between KOLs: ")
            #ask for user name again
    printed=False #set condition for the following loop
    for i in range (0,len(KOL)-1):
        for j in range (i+1,len(KOL)):
            if isFriend(KOL[i],KOL[j])==True: #check friend
                print("Friendship exists between KOLs\n"
                      "For example, "+KOL[i]+" and "+KOL[j]+" are friends")
                printed=True #friendship is found
                break #stop looping 
        if printed==True: 
            break #same as above
    if printed==False: #if no friendship is found
        print("Friendship does not exist between KOLs based on your information.")
        #tell the function user no friendship

def startup():
    T,p=0,0.25
    print('This is the function to determine "KOLs" and existance of friendship between them.\n'
          "To qualify as a KOL, the person should\n"
          "(1) have posted more influential articles than others\n"
          "(normally at most "+str(p)+"% of people can be KOL)\n" 
          "AND (2) the total influence should reach a minimum threshold "+str(T)+'.')
          #introduction to function users
    print("Start with your different commands\n"
          '"u" to input user informations by keyboard\n'
          '"a" to input information of articles by keyboard\n'
          '"f" to input relationship (friends) for a pair of users\n'
          '"m" to determine "KOLs" and the existance of friendship between them according to the information input\n'
          '"s" to stop the function')
    com=input("Enter your command: ")
    while com!='s': #under any circumstances execpt stop the function
        if com=='u':
            data=reg() #function to input user info
        elif com=='a':
            article() #function to input article info
        elif com=='f':
            data=setFd() #function to input friendship info
        elif com=='m':
            main() #main function about KOLs and friendship
        else:
            print("Wrong command") #tell function user that he inputs wrong
        com=input("Enter your command: ")
        #for any conditions, the function user needs to continue to input command
    print("Thanks for using!\n"
          "You can input another set of data by entering 'startup()'")
    #the function ends
startup()
