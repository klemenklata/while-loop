# while-loop

# The example below uses FastAPI endpoint as a local query

i=$(curl http://127.0.0.1:8000/ | awk -F':' '{ print $2 }' | sed 's/}//')

while [ $i -lt 2 ]
do
  echo "HDFS is restarting..."
  sleep 3
  i=$(curl http://127.0.0.1:8000/ | awk -F':' '{ print $2 }' | sed 's/}//')
  if [[ "$i" == '2' ]]; then
    break
  fi
done

echo 'HDFS Started Successuflly!!'
