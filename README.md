# -filename = r"F:\TEST\data.csv"
def get_line():
    line=list(input().split())
    return (int(line[0]),line[1],line[2],int(line[3]),int(line[4]),int(line[5]))
def insert(line):
    if line not in data:
        data.append(line)
def write_to_file(filename):
    with open(filename, 'w') as file:
        file.write(','.join(columns))
        for line in data:
            line=[str(i) for i in line]
            file.write(','.join(line)+'\n')
def read_to_file(filename):
    with open(filename, 'r') as file:
        columns = tuple(file.readline().split(','))
        data = []
        for line in file:
            line = line.split(',')
            data.append((int(line[0]),line[1],line[2],int(line[3]),int(line[4]),int(line[5])))
        return columns, data
def print_data():
    m=max([len(i) for i in columns])
    for i in columns:
        print(str(i).ljust(m+1, ' '), end = '')
    print()
    for line in data:
        for i in line:
            print(str(i).ljust(m+1, ' '), end = '')
        print()
global data, columns
columns, data = read_to_file(filename)
insert(get_line())
write_to_file(filename)
print_data()
