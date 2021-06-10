# Creating-an-application

# Creating an application

#Using the python lambda function for structuring queries
def lambda_handler(event, context):
    first_name = event['queryStringParameters']['first_name']
    last_name = event['queryStringParameters']['last_name']
    order_qty = event['queryStringParameters']['order_qty']

# Defining variables for the pack sizes
my_var = pack_a = 5000
my_var = pack_b = 2000
my_var = pack_c = 1000
my_var = pack_d = 500
my_var = pack_e = 250

#Using validation to ensure only integers are inputted and not any other values

while True:
    try: 
        number_of_items = int(input ('How many items would you like to ship?: '))
        break
    except ValueError:
        print("Please enter a number: ")


# Using division for number of items that are the same as the number of pack sizes because using minus number_of_items to pack_sizes will give 0

if number_of_items == pack_a:
    total_packs = number_of_items / pack_a
    print (total_packs)
    
# If user-input greater than a pack_size variable then using minus to give remainder which can then be minused from the next pack sizes

elif number_of_items > pack_a:
    pack_size = number_of_items - pack_a
    print(pack_size)
remainder1 = pack_b - pack_size
total_packs = remainder1
print(total_packs)

#If user-input less than the first pack variable then use pack_b. 

elif number_of_items < pack_a: 
pack_size = number_of_items - pack_b
remainder2 =  number_of_items - pack_c
total_packs = remainder2
print(total_packs)

# Using division for user-input that are the same as the number of pack sizes for the next pack
if number_of_items == pack_b:
    total_packs = number_of_items / pack_a
    print (total_packs)

# If number_of_items less than pack_b use pack_c.

if number_of_items < pack_b :
    pack_size = number_of_items - pack_c
remainder3 = number_of_items - pack_d
total_packs = remainder3
print(total_packs)

# using division for user-input that is the same as the pack size variables for the next pack

if number_of_items == pack_c:
    total_packs = number_of_items / pack_a
    print (total_packs)

# if number_of_items less than pack_c use pack_d. 
if number_of_items < pack_c :
 pack_size = number_of_items - pack_d
remainder4 = number_of_items - pack_e
total_packs = remainder4
print(total_packs)



# Using division for number of items that are the same as the number of pack sizes for the next pack
if number_of_items == pack_d:
    total_packs = number_of_items / pack_d
    print (total_packs)

#If number of items less than pack_d use pack_e
if number_of_items < pack_d :
pack_size = number_of_items - pack_e
total_packs = pack_size
print(total_packs)



#If user-input less than pack_e then print only one pack
if number_of_items < pack_e:
    print ("1 pack will be sent to you")



#creating the responseObject
app_response for response to user-input
app_response = {}
app_response['message'] = 'Welcome ' + first_name + ' ' + last_name + ', thank you for accessing this app!'
app_response['order_qty'] = 'You have ordered ' + order_qty
app_response['package'] = 'You will receive a package of ' + package

#creating the http responseObject
responseObject = {}
responseObject['statusCode'] = 200
responseObject['headers'] = {}
responseObject['headers']['Content-Type'] = 'application/json'
responseObject['body'] = json.dumps(app_response)
   return responseObject


