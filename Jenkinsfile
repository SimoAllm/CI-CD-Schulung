
pipeline
{
	agent any
	
    options
    {
		timeout(time: 1, units: ‘MINUTES’)
	}

	environment
    {
		var1 = "Hugo"
		var2 = 42
	}

	stages
    {
		stage(‘stage1’)
        {
            steps
            {
                step
                {
                    echo “Var1 hat den Wert ${var1}”
                }
            }
        }
	}
}
