from termcolor import colored
from functions import *
import string
Values = {}
Values['']=''
def infixToPostfix(infixexpr):
    prec = {}
    prec["*"] = 3
    prec["/"] = 3
    prec["+"] = 2
    prec["-"] = 2
    prec["("] = 1
    opStack = Stack()
    postfixList = []
    tokenList = infixexpr.split()

    for token in tokenList:
        if token in "ABCDEFGHIJKLMNOPQRSTUVWXYZ" or token in "0123456789":
            postfixList.append(token)
        elif token == '(':
            opStack.push(token)
        elif token == ')':
            topToken = opStack.pop()
            while topToken != '(':
                postfixList.append(topToken)
                topToken = opStack.pop()
        else:
            while (not opStack.isEmpty()) and \
               (prec[opStack.peek()] >= prec[token]):
                  postfixList.append(opStack.pop())
            opStack.push(token)

    while not opStack.isEmpty():
        postfixList.append(opStack.pop())
    return " ".join(postfixList)

def main():
  		
    i=1
    while True:
        try:
	    t='In [' + str(i) + ']: '
	    t=colored(t,'blue')
            text = raw_input(t)
	    word=text.split(' ')
		############################## CALCULATIONS #####################################################
	    if ("+" in text) or ("-" in text) or ("*" in text) or ("/" in text) or ("**" in text) or ("^" in text) or ("%" in text):
			#result=Interpreter_calc(text)			
			alpha=0
			al=0
			for alpha in range(0,25):
				if string.lowercase[alpha] in text:
					al=1
			try:
				if al:
					var=''
					Var=[]
					PostFix=[]
					flagg=0		
					v=0	
					PostFix=infixToPostfix(text)
					for ii in range(0,len(PostFix)	):
						if PostFix[ii] not in "0123456789+-*/%^":
							var = var + PostFix[ii]
							#print var
							flagg=1
						else:
							if flagg:
								flagg=0
								#print var
								#print text
								text=string.replace(text,var,str(Values[var]))
									#print text							
								#print Values[var]
								var=''
					#print var		 
					text=string.replace(text,var,str(Values[var]))
					#text.replace(var,Value[var])
					#print text
					#print "+-*/%^"
			except:
				print "Variables Given in the Expression were not Defined\n"
				continue
			result=eval(text)			
			t='Out['+ str(i) + ']: '
			t=colored(t,'red')
        		print t + str(int(result)) + '\n'				
#***********************JUST COMMAND ******************************#

	    else:
			if text == "quit":
				print
				break
			else:	
				t='Out['+str(i) + ']: '
				t=colored(t,'red')
				print t + str(Values[text]) + '\n'
				i=i+1
				continue
        except EOFError:
		temp='\n'+ "Want to exit ([y]/n)?"
		te = raw_input(temp)
		if te == 'y':
			break
		else:
			continue		        
		
        i= i+1
    
if __name__ == '__main__':
    main()
