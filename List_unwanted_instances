import boto3
import csv
def SG(writer):
  client = boto3.client('ec2', region_name="eu-west-1", aws_access_key_id=accesskey, aws_secret_access_key=secretkey)
  
  dict01={}
  list_inst = client.describe_instances()
  for i in list_inst['Reservations']:
  #print(i)
    for j in i['Instances']:
    #print(j['InstanceId'], j['LaunchTime'], j['State'])
      dict01["InstanceId"] = j['InstanceId']
      dict01["LaunchTime"] = j['LaunchTime']
      dict01["State"]= j['State']
      writer.writerow(dict01)
  print("CSV for running instances created successfully")

def main():
 fieldnames = ["InstanceId","LaunchTime","State"]
 file_name = "dict01.csv"
 with open (file_name,"w",newline='') as csv_file:
  writer = csv.DictWriter(csv_file,fieldnames=fieldnames)
  writer.writeheader()
  SG(writer)
main()

