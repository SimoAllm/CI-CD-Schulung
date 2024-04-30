pipeline
{
    agent any

    options
    {
        timeout(time: 1, unit: 'MINUTES')
    }

    environment
    {
        var1 = 'Hugo'
        var2 = '42'
    }

    stages
    {
        stage('stage1')
        {
            steps
            {
                echo "Var1 hat den Wert ${env.var1}"
            }
        }
    }
}
